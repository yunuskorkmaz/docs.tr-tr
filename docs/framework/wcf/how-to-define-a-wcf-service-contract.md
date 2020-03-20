---
title: 'Öğretici: Windows Communication Foundation hizmet sözleşmesi tanımlayın'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 7c1c42c4f22a1a9627c147440e8e198551470b7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184086"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Öğretici: Windows Communication Foundation hizmet sözleşmesi tanımlayın

Bu öğretici, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevden ilkini açıklar. Öğreticilere genel bir bakış için [Bkz. Öğretici: Windows Communication Foundation uygulamalarıyla başlayın.](getting-started-tutorial.md)

Bir WCF hizmeti oluşturduğunuzda, ilk göreviniz bir hizmet sözleşmesi tanımlamaktır. Hizmet sözleşmesi, hizmetin hangi işlemleri desteklediğini belirtir. Bir işlem bir Web hizmeti yöntemi olarak düşünülebilir. C# veya Visual Basic arabirimi tanımlayarak hizmet sözleşmeleri oluşturursunuz. Arabirim aşağıdaki özelliklere sahiptir:

- Arabirimdeki her yöntem belirli bir hizmet işlemine karşılık gelir.
- Her arabirim için özniteliği uygulamanız <xref:System.ServiceModel.ServiceContractAttribute> gerekir.
- Her işlem/yöntem için özniteliği <xref:System.ServiceModel.OperationContractAttribute> uygulamanız gerekir.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> - Bir **WCF Hizmet Kitaplığı** projesi oluşturun.
> - Bir hizmet sözleşmesi arabirimi tanımlayın.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Bir WCF Hizmet Kitaplığı projesi oluşturun ve bir hizmet sözleşmesi arabirimi tanımlayın

1. Yönetici olarak Visual Studio'u açın. Bunu yapmak için **Başlat** menüsünde Visual Studio programını seçin ve ardından kısayol menüsünden yönetici olarak **Daha Fazla** > **Çalıştır'ı** seçin.

2. Bir **WCF Hizmet Kitaplığı** projesi oluşturun.

   1. **Dosya** menüsünden **Yeni** > **Proje'yi**seçin.

   2. Yeni **Proje** iletişim kutusunda, sol tarafta Visual **C#** veya **Visual Basic'i**genişletin ve ardından **WCF** kategorisini seçin. Visual Studio pencerenin orta bölümünde proje şablonlarının listesini görüntüler. **WCF Hizmet Kitaplığı'nı**seçin.

      > [!NOTE]
      > **WCF** proje şablonu kategorisini görmüyorsanız, Visual Studio'nun **Windows Communication Foundation** bileşenini yüklemeniz gerekebilir. Yeni **Proje** iletişim kutusunda, sol taraftaki **Görsel Stüdyo Yükleyicisini Aç** bağlantısını seçin. Bireysel **bileşenler** sekmesini seçin ve ardından **Geliştirme etkinlikleri** kategorisi altında Windows **Communication Foundation'ı** bulup seçin. Bileşeni yüklemeye başlamak için **Değiştir'i** seçin.

   3. Pencerenin alt bölümünde, **Ad** için *BaşlangıçAl'ı* ve **Çözüm adı**için *Başlangıç'ı* girin.

   4. **Tamam'ı**seçin.

      Visual Studio üç dosyavardır proje oluşturur: *IService1.cs* (veya *IService1.vb* Visual Basic proje için), *Service1.cs* (veya *Service1.vb* Visual Basic proje için) ve *App.config*. Visual Studio bu dosyaları aşağıdaki gibi tanımlar:
      - *IService1* dosyası, hizmet sözleşmesinin varsayılan tanımını içerir.
      - *Service1* dosyası, hizmet sözleşmesinin varsayılan uygulamasını içerir.
      - *App.config* dosyası Visual Studio WCF Service Host aracı ile varsayılan hizmet yüklemek için gerekli yapılandırma bilgilerini içerir. WCF Service Host aracı hakkında daha fazla bilgi için [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)bakın.

      > [!NOTE]
      > Visual Basic geliştirici ortamı ayarlarıyla Visual Studio'yu yüklediyseniz, çözüm gizlenmiş olabilir. Bu durumda, **Araçlar** menüsünden **Seçenekler'i** seçin ve **Ardından Seçenekler** penceresinde Projeler **ve Çözümler** > **Genel'i** seçin. **Her Zaman çözüm göster'i**seçin. Ayrıca, **oluşturulduğunda yeni projeleri kaydet** seçildiğini doğrulayın.

3. **Solution Explorer'dan** **IService1.cs** veya **IService1.vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
            public interface ICalculator
            {
                [OperationContract]
                double Add(double n1, double n2);
                [OperationContract]
                double Subtract(double n1, double n2);
                [OperationContract]
                double Multiply(double n1, double n2);
                [OperationContract]
                double Divide(double n1, double n2);
            }
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     Bu sözleşme bir çevrimiçi hesap makinesi tanımlar. `ICalculator` Arabirimin <xref:System.ServiceModel.ServiceContractAttribute> öznitelik ile işaretlendiğini fark edin (basitleştirilmiş olarak). `ServiceContract` Bu öznitelik, sözleşme adını ayrıştırmak için bir ad alanı tanımlar. Kod, her hesap makinesi <xref:System.ServiceModel.OperationContractAttribute> işlemini öznitelik `OperationContract`ile işaretler (basitleştirilmiş olarak).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Bir WCF Hizmet Kitaplığı projesi oluşturun.
> - Bir hizmet sözleşmesi arabirimi tanımlayın.

WCF hizmet sözleşmesini nasıl uygulayacağınızı öğrenmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: WCF hizmet sözleşmesi uygulayın](how-to-implement-a-wcf-contract.md)
