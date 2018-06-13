---
title: 'Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF clients [WCF], using
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 79431588e27b02a40d5898929f1bdf644c8a79cd
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803812"
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a>Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Kullanma
Son altı görevlerin temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken budur. Tüm altı görevlerinin genel bakış için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.  
  
 Windows Communication Foundation (WCF) proxy oluşturulan ve yapılandırılan sonra istemci örneği oluşturulabilir ve istemci uygulaması derlenmiş ve WCF Hizmeti ile iletişim kurmak için kullanılan. Bu konuda başlatmasını ve WCF istemcisi kullanarak yordamlar açıklanmaktadır. Bu yordam üç şey yapar:  
  
1.  Bir WCF istemcisi başlatır.  
  
2.  Hizmet işlemleri oluşturulan proxy sunucudan çağırır.  
  
3.  İşlem çağrısı tamamlandığında istemci kapatır.  
  
### <a name="to-use-a-windows-communication-foundation-client"></a>Windows Communication Foundation istemcisi kullanmak için  
  
1.  GettingStartedClient projesinden Program.cs veya Program.vb dosyasını açın ve var olan kodu aşağıdaki kodla değiştirin:  
  
    ```  
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
  
                //Step 3: Closing the client gracefully closes the connection and cleans up resources.  
                client.Close();  
            }  
        }  
    }  
    ```  
  
    ```  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Text  
    Imports System.ServiceModel  
    Imports GettingStartedClientVB2.ServiceReference1  
  
    Module Module1  
  
        Sub Main()  
            ' Step 1: Create an instance of the WCF proxy  
            Dim Client As New CalculatorClient()  
  
            'Step 2: Call the service operations.  
            'Call the Add service operation.  
            Dim value1 As Double = 100D  
            Dim value2 As Double = 15.99D  
            Dim result As Double = Client.Add(value1, value2)  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Subtract service operation.  
            value1 = 145D  
            value2 = 76.54D  
            result = Client.Subtract(value1, value2)  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Multiply service operation.  
            value1 = 9D  
            value2 = 81.25D  
            result = Client.Multiply(value1, value2)  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Divide service operation.  
            value1 = 22D  
            value2 = 7D  
            result = Client.Divide(value1, value2)  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)  
  
            ' Step 3: Closing the client gracefully closes the connection and cleans up resources.  
            Client.Close()  
  
            Console.WriteLine()  
            Console.WriteLine("Press <ENTER> to terminate client.")  
            Console.ReadLine()  
  
        End Sub  
  
    End Module  
    ```  
  
     GettingStartedClient.ServiceReference1 alır kullanarak veya Imports deyimi dikkat edin. Visual Studio'da hizmet Başvurusu Ekle tarafından oluşturulan kodu alır. Kod WCF proxy başlatır ve ardından her hesaplayıcı hizmeti tarafından sunulan hizmet işlemlerinin çağırır, proxy kapatır ve sonlandırır.  
  
 Şimdi öğreticisini tamamladınız. Bir hizmet sözleşmesini tanımlı, hizmet sözleşmesi uygulanan, WCF proxy oluşturulan, WCF istemci uygulaması yapılandırılmış ve proxy hizmet işlemlerini çağırma kullanılacak. Uygulamayı test etmek için önce hizmeti başlatmayı GettingStartedHost çalıştırın ve ardından GettingStartedClient çalıştırın. GettingStartedHost çıkışı aşağıdaki gibi görünmelidir:  
  
```Output  
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714  
```  
  
 GettingStartedClient çıkışı aşağıdaki gibi görünmelidir:  
  
```Output  
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemci Derleme](../../../docs/framework/wcf/building-clients.md)  
 [Nasıl yapılır: İstemci Oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Temel WCF Programlama](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Nasıl yapılır: Çift Yönlü Anlaşma Oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Başlarken](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Kendini Barındırma](../../../docs/framework/wcf/samples/self-host.md)
