---
title: 'Öğretici: Bir Windows Communication Foundation Hizmet sözleşmesini uygulama'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: fa8c5457c636d7f37215f0d4b4fdbb1c96c9481e
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463624"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Öğretici: Bir Windows Communication Foundation Hizmet sözleşmesini uygulama

Bu öğreticide, temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görev ikinci açıklanmaktadır. Öğreticiler genel bakış için bkz. [Öğreticisi: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).

WCF uygulaması oluşturmak için sonraki adım, önceki adımda oluşturduğunuz WCF Hizmeti arabirim uygulamak için kod eklemektir. Bu adımda, adlı bir sınıf oluşturun `CalculatorService` uygulayan kullanıcı tanımlı `ICalculator` arabirimi. Aşağıdaki kod her bir yöntemin hesaplayıcı işlemi çağırır ve metin test etmek için konsola yazar. 

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> - WCF hizmet sözleşmesini uygulama için kod ekleyin.
> - Çözümü oluşturun.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>WCF hizmet sözleşmesini uygulama için kod ekleyin

İçinde **GettingStartedLib**açın **Service1.cs** veya **Service1.vb** dosya ve kendi kodu aşağıdaki kodla değiştirin:

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

## <a name="edit-appconfig"></a>App.config Düzenle

Düzen **App.config** içinde **GettingStartedLib** koda yapılan değişiklikleri yansıtacak şekilde.
- Görsel için C# projeleri:
  - 14. satır için değiştirin `<service name="GettingStartedLib.CalculatorService">`
  - 17 satırına değiştirme `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Satır 22 için değiştirin `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Visual Basic projeleri için:
  - 14. satır için değiştirin `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - 17 satırına değiştirme `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Satır 22 için değiştirin `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Kod derleme

Derleme hataları doğrulamak için çözümü oluşturun. Visual Studio kullanıyorsanız **derleme** menüsünü seçin **Çözümü Derle** (veya basın **Ctrl**+**Shift** + **B**).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> - WCF hizmet sözleşmesini uygulama için kod ekleyin.
> - Çözümü oluşturun.

WCF hizmeti çalıştırmaya hakkında bilgi edinmek için sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: Temel bir WCF Hizmeti barındırma ve çalıştırma](how-to-host-and-run-a-basic-wcf-service.md)
