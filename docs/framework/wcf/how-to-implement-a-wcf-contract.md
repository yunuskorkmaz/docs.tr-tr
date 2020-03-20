---
title: 'Öğretici: Windows Communication Foundation hizmet sözleşmesi uygulama'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: debdeeac7064f5bae21622b2d9de84a4d8a0e66f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184061"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Öğretici: Windows Communication Foundation hizmet sözleşmesi uygulama

Bu öğretici, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevin ikincisini açıklar. Öğreticilere genel bir bakış için [Bkz. Öğretici: Windows Communication Foundation uygulamalarıyla başlayın.](getting-started-tutorial.md)

WCF uygulaması oluşturmak için bir sonraki adım, önceki adımda oluşturduğunuz WCF hizmet arabirimini uygulamak için kod eklemektir. Bu adımda, kullanıcı tanımlı `CalculatorService` `ICalculator` arabirimi uygulayan adlandırılmış bir sınıf oluşturursunuz. Aşağıdaki koddaki her yöntem bir hesap makinesi işlemi çağırır ve bunu test etmek için konsola metin yazar.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> - WCF hizmet sözleşmesini uygulamak için kod ekleyin.
> - Çözümü derleyin.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>WCF hizmet sözleşmesini uygulamak için kod ekleme

**GettingStartedLib'de** **Service1.cs** veya **Service1.vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:

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

## <a name="edit-appconfig"></a>App.config'i edit

Kodda yaptığınız değişiklikleri yansıtmak için **GettingStartedLib'de** **App.config'i** edin.

- Görsel C# projeleri için:
  - Satır 14'te değiştir`<service name="GettingStartedLib.CalculatorService">`
  - Satır 17'yi değiştir`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Satır 22'yi değiştir`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Visual Basic projeleri için:
  - Satır 14'te değiştir`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - Satır 17'yi değiştir`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Satır 22'yi değiştir`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Kodu derleme

Derleme hatası olmadığını doğrulamak için çözüm oluşturun. Visual Studio kullanıyorsanız, **Yapı** menüsünde **Çözüm Oluştur'u** seçin (veya **Ctrl**+**Shift**+**B**tuşuna basın).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - WCF hizmet sözleşmesini uygulamak için kod ekleyin.
> - Çözümü derleyin.

WCF hizmetini nasıl çalıştıracağımıöğrenmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: Ana bilgisayar ve temel bir WCF hizmeti çalıştırın](how-to-host-and-run-a-basic-wcf-service.md)
