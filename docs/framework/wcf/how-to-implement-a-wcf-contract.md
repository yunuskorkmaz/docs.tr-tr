---
title: 'Öğretici: Windows Communication Foundation hizmet sözleşmesi uygulama'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 05923dc0a2223da5e5fcda483abc1ee1dd2d643f
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928706"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Öğretici: Windows Communication Foundation hizmet sözleşmesi uygulama

Bu öğreticide, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevin ikinci açıklaması açıklanmaktadır. Öğreticilere genel bakış için bkz [. Öğretici: Windows Communication Foundation uygulamaları](getting-started-tutorial.md)ile çalışmaya başlayın.

Bir WCF uygulaması oluşturmaya yönelik sonraki adım, önceki adımda oluşturduğunuz WCF hizmeti arabirimini uygulamak için kod eklemektir. Bu adımda, Kullanıcı tanımlı `CalculatorService` `ICalculator` arabirimi uygulayan adlı bir sınıf oluşturursunuz. Aşağıdaki koddaki her bir yöntem bir Hesaplayıcı işlemini çağırır ve test etmek üzere konsola metin yazar. 

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> - WCF hizmet sözleşmesini uygulamak için kod ekleyin.
> - Çözümü oluşturun.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>WCF hizmet sözleşmesini uygulamak için kod ekleme

**GettingStartedLib**içinde **Service1.cs** veya **Service1. vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:

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

## <a name="edit-appconfig"></a>App. config dosyasını Düzenle

Kodda yaptığınız değişiklikleri yansıtmak için **GettingStartedLib** içinde **app. config dosyasını** düzenleyin.

- Görsel C# projeler için:
  - 14 satırı olarak değiştir`<service name="GettingStartedLib.CalculatorService">`
  - 17. satırı olarak değiştir`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Satır 22 ' i Değiştir`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Visual Basic projeleri için:
  - 14 satırı olarak değiştir`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - 17. satırı olarak değiştir`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Satır 22 ' i Değiştir`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Kod derleme

Herhangi bir derleme hatası olmadığını doğrulamak için çözümü oluşturun. Visual Studio kullanıyorsanız, **Yapı** menüsünde **Build Solution** (veya **CTRL**+**SHIFT**+**B**tuşlarına basın) öğesini seçin.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - WCF hizmet sözleşmesini uygulamak için kod ekleyin.
> - Çözümü oluşturun.

WCF hizmetini çalıştırmayı öğrenmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: Temel bir WCF hizmetini barındırma ve çalıştırma](how-to-host-and-run-a-basic-wcf-service.md)
