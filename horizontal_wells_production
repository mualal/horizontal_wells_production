import math
import numpy as np
from matplotlib import pyplot as plt


def productivity(L=None, k=40*10**(-15), h=10, dp=10**7, Rk=2000, rc=0.14, mu=20.8*(10**(-3)), S=3):
    def Joshi(well_length):
        L_half = well_length / 2
        a = L_half * math.sqrt(1 / 2 + math.sqrt(1 / 4 + (2 * Rk / well_length) ** 4))
        Q = (2 * math.pi * k * h * dp) / mu
        first = math.log((a + math.sqrt(a ** 2 - L_half ** 2)) / L_half)
        second = h / well_length * math.log(h / (2 * math.pi * rc))
        Q = Q / (first + second + S)
        return Q * 86400

    if L == None:
        max_L = 2000
        x = np.linspace(1, max_L, max_L)
        y = []
        flag = False
        for i in range(max_L):
            y.append(Joshi(x[i]))
            if i > 1 and flag is False:
                if (y[i - 1] - y[i - 2])/(x[i - 1] - x[i - 2])*500 < 3:
                    print('Оптимальная длина: ' + str(x[i]))
                    print('Дебит при оптимальной длине: ' + str(y[i]))
                    flag = True
        plt.plot(x, y, color = 'black')
        plt.grid()
        plt.title('Зависимость дебита от длины ГС')
        plt.xlabel('Длина горизонтальной скважины, $м$')
        plt.ylabel('Дебит горизонтальной скважины, $м^3/сут.$')
        plt.show()
    else:
        print(Joshi(L))


productivity()
