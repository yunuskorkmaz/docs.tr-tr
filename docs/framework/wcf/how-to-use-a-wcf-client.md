---
title: 'Öğretici: Windows Communication Foundation istemcisi kullanma'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 5c280933c81ef54ba58181e3005e30775b9b8e42
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928895"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>Öğretici: Windows Communication Foundation istemcisi kullanma

Bu öğreticide, temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevin son açıklaması açıklanır. Öğreticilere genel bakış için bkz [. Öğretici: Windows Communication Foundation uygulamaları](getting-started-tutorial.md)ile çalışmaya başlayın.

Bir Windows Communication Foundation (WCF) proxy oluşturup yapılandırdıktan sonra, bir istemci örneği oluşturup istemci uygulamasını derleyebilirsiniz. Daha sonra WCF hizmeti ile iletişim kurmak için kullanabilirsiniz. 

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> - WCF istemcisini kullanmak için kod ekleyin.
> - WCF istemcisini test edin.

## <a name="add-code-to-use-the-wcf-client"></a>WCF istemcisini kullanmak için kod ekleme

İstemci kodu aşağıdaki adımları yapar:

- WCF istemcisini başlatır.
- Oluşturulan proxy 'den hizmet işlemlerini çağırır.
- İşlem çağrısı tamamlandıktan sonra istemciyi kapatır.

**GettingStartedClient** projesinden **program.cs** veya **Module1. vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:

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

İçeri aktaran `using` C# (görsel`Imports` için) veya (for Visual Basic) bildirimine dikkat edin. `GettingStartedClient.ServiceReference1` Bu ifade, Visual Studio 'Nun **hizmet başvurusu Ekle** işleviyle oluşturduğu kodu içeri aktarır. Kod, WCF ara sunucusunu başlatır ve hesap makinesi hizmetinin sunduğu hizmet işlemlerinin her birini çağırır. Ardından, proxy 'yi kapatır ve programı sonlandırır.

## <a name="test-the-wcf-client"></a>WCF istemcisini test etme

### <a name="test-the-application-from-visual-studio"></a>Uygulamayı Visual Studio 'dan test etme

1. Çözümü kaydedin ve oluşturun.

2. **GettingStartedLib** klasörünü seçin ve ardından kısayol menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.

3. **Başlangıç projeleri**' nden, açılan listeden **GettingStartedLib** ' i seçin, sonra **Çalıştır** ' ı seçin veya **F5**tuşuna basın.

### <a name="test-the-application-from-a-command-prompt"></a>Uygulamayı bir komut isteminden test etme

1. Yönetici olarak bir komut istemi açın ve ardından Visual Studio çözüm dizininize gidin. 

2. Hizmeti başlatmak için: *Gettingstartedhost\bin\debug\gettingstartedhost.exe*girin.

3. İstemcisini başlatmak için: Başka bir komut istemi açın, Visual Studio çözüm dizininize gidin ve *Gettingstartedclient\bin\debug\gettingstartedclient.exe*yazın.

   *GettingStartedHost. exe* aşağıdaki çıktıyı üretir:

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

   *GettingStartedClient. exe* aşağıdaki çıktıyı üretir:

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>Sonraki adımlar

Artık WCF başlangıç öğreticisindeki tüm görevleri tamamladınız. Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> - WCF istemcisini kullanmak için kod ekleyin.
> - WCF istemcisini test edin.

Adımlardan birinde sorun veya hatalar varsa, bunları gidermek için sorun giderme makalesindeki adımları izleyin.

> [!div class="nextstepaction"]
> [WCF öğreticileri ile çalışmaya başlama hakkında sorun giderme](troubleshooting-the-getting-started-tutorial.md)
