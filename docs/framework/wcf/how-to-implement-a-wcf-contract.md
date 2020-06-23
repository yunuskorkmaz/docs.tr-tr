---
title: 'Öğretici: Windows Communication Foundation hizmet sözleşmesi uygulama'
description: WCF uygulaması oluşturmaya başlamanıza yardımcı olan bir makale serisinin parçası olarak bir WCF hizmeti arabirimini uygulamak için kod ekleme hakkında bilgi edinin.
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 89f97610cccd42c2a5d298baa667327d077fd472
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244653"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Öğretici: Windows Communication Foundation hizmet sözleşmesi uygulama

Bu öğreticide, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevin ikinci açıklaması açıklanmaktadır. Öğreticilere genel bakış için bkz. [öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).

Bir WCF uygulaması oluşturmaya yönelik sonraki adım, önceki adımda oluşturduğunuz WCF hizmeti arabirimini uygulamak için kod eklemektir. Bu adımda, `CalculatorService` Kullanıcı tanımlı arabirimi uygulayan adlı bir sınıf oluşturursunuz `ICalculator` . Aşağıdaki koddaki her bir yöntem bir Hesaplayıcı işlemini çağırır ve test etmek üzere konsola metin yazar.

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:
> [!div class="checklist"]
>
> - WCF hizmet sözleşmesini uygulamak için kod ekleyin.
> - Çözümü derleyin.

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

## <a name="edit-appconfig"></a>App.config Düzenle

Kodda yaptığınız değişiklikleri yansıtmak için **GettingStartedLib** içindeki **App.config** düzenleyin.

- Visual C# projeleri için:
  - 14 satırı olarak değiştir`<service name="GettingStartedLib.CalculatorService">`
  - 17. satırı olarak değiştir`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Satır 22 ' i Değiştir`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Visual Basic projeleri için:
  - 14 satırı olarak değiştir`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - 17. satırı olarak değiştir`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Satır 22 ' i Değiştir`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Kodu derle

Herhangi bir derleme hatası olmadığını doğrulamak için çözümü oluşturun. Visual Studio kullanıyorsanız, **Yapı** menüsünde **Build Solution** (veya **CTRL** + **SHIFT** + **B**tuşlarına basın) öğesini seçin.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - WCF hizmet sözleşmesini uygulamak için kod ekleyin.
> - Çözümü derleyin.

WCF hizmetini çalıştırmayı öğrenmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: temel bir WCF hizmetini barındırma ve çalıştırma](how-to-host-and-run-a-basic-wcf-service.md)
