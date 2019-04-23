---
title: 'Öğretici: Bir Windows Communication Foundation istemcisi kullanma'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: fa9aa3612a8dc72623fc4ea4b1ea337ac773fa26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169981"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>Öğretici: Bir Windows Communication Foundation istemcisi kullanma

Bu öğreticide, temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görev son açıklanmaktadır. Öğreticiler genel bakış için bkz. [Öğreticisi: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).

Oluşturduğunuz ve Windows Communication Foundation (WCF) proxy yapılandırılan sonra bir istemci örneği oluşturun ve istemci uygulamayı derleyin. Ardından, WCF Hizmeti ile iletişim kurmak için kullanabilirsiniz. 

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> - WCF istemcisini kullanmak için kodu ekleyin.
> - WCF istemcisini test edin.

## <a name="add-code-to-use-the-wcf-client"></a>WCF istemcisini kullanmak için kodu ekleyin

İstemci kodu, aşağıdaki adımları gerçekleştirir:
- WCF istemcisi örneği oluşturur.
- Hizmet işlemleri üretilen Ara sunucuya çağırır.
- İşlem çağrısı tamamlandıktan sonra istemci kapatır.

Açık **Program.cs** veya **Module1.vb** dosya **GettingStartedClient** proje ve onun kodu aşağıdaki kodla değiştirin:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GettingStartedClient.ServiceReference1;

namespace GettingStartedClient
{
    class Program
    {
        static void Main(string[] args)
        {
            //Step 1: Create an instance of the WCF proxy.
            CalculatorClient client = new CalculatorClient();

            // Step 2: Call the service operations.
            // Call the Add service operation.
            double value1 = 100.00D;
            double value2 = 15.99D;
            double result = client.Add(value1, value2);
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

            // Call the Subtract service operation.
            value1 = 145.00D;
            value2 = 76.54D;
            result = client.Subtract(value1, value2);
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

            // Call the Multiply service operation.
            value1 = 9.00D;
            value2 = 81.25D;
            result = client.Multiply(value1, value2);
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

            // Call the Divide service operation.
            value1 = 22.00D;
            value2 = 7.00D;
            result = client.Divide(value1, value2);
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

            // Step 3: Close the client to gracefully close the connection and clean up resources.
            Console.WriteLine("\nPress <Enter> to terminate the client.");
            Console.ReadLine();
            client.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.ServiceModel
Imports GettingStartedClient.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy.
        Dim Client As New CalculatorClient()

        ' Step 2: Call the service operations.
        ' Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        ' Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        ' Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        ' Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Close the client to gracefully close the connection and clean up resources.
        Console.WriteLine()
        Console.WriteLine("Press <Enter> to terminate the client.")
        Console.ReadLine()
        Client.Close()

    End Sub

End Module
```

Bildirim `using` (görsel için C#) veya `Imports` (Visual Basic için) Imports deyimi `GettingStartedClient.ServiceReference1`. Visual Studio ile oluşturulan kodu bu açıklamayı **hizmet Başvurusu Ekle** işlevi. Kod, WCF proxy başlatır ve hesaplayıcı hizmetini gösteren service işlemlerden her biriyle çağırır. Ardından, proxy kapatır ve program sona erer.

## <a name="test-the-wcf-client"></a>WCF istemcisini test etme

### <a name="test-the-application-from-visual-studio"></a>Uygulamayı Visual Studio'dan Test etme

1. Kaydet ve Çözümü derleyin.

2. Seçin **GettingStartedLib** klasöre tıklayın ve ardından **başlangıç projesi olarak ayarla** kısayol menüsünden.

3. Gelen **başlangıç projelerini**seçin **GettingStartedLib** aşağı açılan listeden seçip **çalıştırma** veya basın **F5**.

### <a name="test-the-application-from-a-command-prompt"></a>Bir komut isteminden uygulamayı test etme

1. Bir yönetici olarak bir komut istemi açın ve ardından, Visual Studio çözüm dizinine gidin. 

2. Hizmeti başlatmak için: Girin *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.

3. İstemcisini başlatmak için: Başka bir komut istemi açın, Visual Studio çözüm dizinine gidin ve ardından girin *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.

   *GettingStartedHost.exe* aşağıdaki çıktıyı üretir:

   ```text
   The service is ready.
   Press <Enter> to terminate the service.

   Received Add(100,15.99)
   Return: 115.99
   Received Subtract(145,76.54)
   Return: 68.46
   Received Multiply(9,81.25)
   Return: 731.25
   Received Divide(22,7)
   Return: 3.14285714285714
   ```

   *GettingStartedClient.exe* aşağıdaki çıktıyı üretir:

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>Sonraki adımlar

WCF başlangıç Öğreticisi artık tüm görevleri tamamladınız. Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> - WCF istemcisini kullanmak için kodu ekleyin.
> - WCF istemcisini test edin.

Sorunlar veya hatalar adımların hiçbirini varsa, bunları gidermek için sorun giderme makalesindeki adımları izleyin.

> [!div class="nextstepaction"]
> [Sorun giderme Get ile WCF Eğitmenleri](troubleshooting-the-getting-started-tutorial.md)
