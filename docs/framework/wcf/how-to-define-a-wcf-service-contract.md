---
title: 'Öğretici: Bir Windows Communication Foundation Hizmet sözleşmesini tanımlama'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: a1908339460191fcb81d03d45c56dd57b2cf4c4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929356"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Öğretici: Bir Windows Communication Foundation Hizmet sözleşmesini tanımlama

Bu öğretici, ilk beş görev temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken açıklar. Öğreticiler genel bakış için bkz. [Öğreticisi: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).

Bir WCF Hizmeti oluşturduğunuzda, ilk göreviniz bir hizmet sözleşmesini tanımlamaktır. Hizmet sözleşmesi hangi işlemleri belirtir destekler. Bir işlem, bir Web hizmeti yöntemi düşünülebilir. Hizmet sözleşmeleri görsel tanımlayarak oluşturduğunuz C# veya Visual Basic (VB) arabirim. Bir arabirim, aşağıdaki özelliklere sahiptir:

- Arabirimdeki her yöntem için bir hizmet işlemiyle karşılık gelir. 
- Her arabirim için uygulamanız gerekir <xref:System.ServiceModel.ServiceContractAttribute> özniteliği.
- Her işlem/yöntem için uygulamalısınız <xref:System.ServiceModel.OperationContractAttribute> özniteliği. 

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> - Oluşturma bir **WCF hizmet Kitaplığı** proje.
> - Bir hizmet sözleşme arabirimi tanımlayın.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Bir WCF hizmet kitaplığı projesi oluşturun ve hizmet sözleşme arabirimi tanımlayın

1. Visual Studio'yu yönetici olarak açın. Bunu yapmak için Visual Studio programda seçin **Başlat** menüsüne ve ardından **daha fazla** > **yönetici olarak çalıştır** kısayol menüsünden.

2. Oluşturma bir **WCF hizmet Kitaplığı** proje.

   1. Gelen **dosya** menüsünde **yeni** > **proje**.

   2. İçinde **yeni proje** iletişim kutusunda sol taraftaki genişletin **Visual C#** veya **Visual Basic**ve ardından **WCF** kategorisi. Visual Studio Proje şablonları listesi penceresinin Merkezi bölümünde görüntüler. Seçin **WCF hizmet Kitaplığı**.

      > [!NOTE]
      > Görmüyorsanız **WCF** proje şablonu kategorisi yüklemeniz gerekebilir **Windows Communication Foundation** Visual Studio bileşen. İçinde **yeni proje** iletişim kutusunda **açık Visual Studio yükleyicisi** sol tarafındaki bağlantıyı. Seçin **tek tek bileşenler** sekmesine ve ardından bulmak ve seçmek **Windows Communication Foundation** altında **geliştirme etkinliklerini** kategorisi. Seçin **Değiştir** bileşeni yüklemeyi başlatmak için.

   3. Pencerenin alt kısmında girin *GettingStartedLib* için **adı** ve *GettingStarted* için **çözüm adı**. 

   4. **Tamam**’ı seçin.

      Visual Studio üç dosyayı içeren projenin oluşturur: *Iservice1.cs* (veya *Iservice1.vb* Visual Basic projesi için), *Service1.cs* (veya *Service1.vb* Visual Basic projesi için), ve  *App.config*. Visual Studio, bu dosyalar gibi tanımlar: 
      - *Iservice1* dosyası varsayılan hizmet sözleşmesi tanımını içerir. 
      - *Service1* varsayılan uygulama hizmet sözleşmesinin dosyası içerir. 
      - *App.config* dosyası Visual Studio WCF hizmet konağı aracıyla varsayılan hizmetini yüklemek için gereken yapılandırma bilgilerini içerir. WCF hizmet konağı aracı hakkında daha fazla bilgi için bkz. [WCF hizmet Konağı (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Visual Basic Geliştirici ortam ayarları ile Visual Studio yüklü değilse, çözüm gizlenmiş olabilir. Bu durumda, seçin **seçenekleri** gelen **Araçları** menüsü, ardından **projeler ve çözümler** > **genel** içinde **seçenekleri** penceresi. Seçin **çözümü her zaman göster**. Ayrıca, doğrulayın **oluşturulduğunda yeni projeleri Kaydet** seçilir.

3. Gelen **Çözüm Gezgini**açın **Iservice1.cs** veya **Iservice1.vb** dosya ve kendi kodu aşağıdaki kodla değiştirin:

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

     Bu sözleşme, çevrimiçi bir hesap makinesi tanımlar. Bildirim `ICalculator` arabirimi ile işaretlenmiş <xref:System.ServiceModel.ServiceContractAttribute> özniteliği (olarak Basitleştirilmiş `ServiceContract`). Bu öznitelik sözleşme adı ayırt etmek için bir ad alanı tanımlar. Her hesap makinesi işlemle kodu işaretler <xref:System.ServiceModel.OperationContractAttribute> özniteliği (olarak Basitleştirilmiş `OperationContract`).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
> - Bir WCF hizmet kitaplığı projesi oluşturun.
> - Bir hizmet sözleşme arabirimi tanımlayın.

WCF hizmet sözleşmesini uygulama konusunda bilgi almak için sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: Bir WCF Hizmeti sözleşmesi uygulama](how-to-implement-a-wcf-contract.md)
