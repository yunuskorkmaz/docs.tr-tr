---
title: 'Öğretici: Windows Communication Foundation hizmet sözleşmesi tanımlama'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 49526808a65b68c6df734bd7f3e76eff1e4a6bc5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338290"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Öğretici: Windows Communication Foundation hizmet sözleşmesi tanımlama

Bu öğreticide, temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevden ilki açıklanmaktadır. Öğreticilere genel bakış için bkz. [öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).

Bir WCF hizmeti oluşturduğunuzda, ilk göreviniz bir hizmet sözleşmesini tanımlamaktır. Hizmet sözleşmesi, hizmetin desteklediği işlemleri belirtir. Bir işlem, bir Web hizmeti yöntemi olarak düşünülebilir. Hizmet sözleşmelerini bir C# veya Visual Basic arabirimi tanımlayarak oluşturursunuz. Bir arabirim aşağıdaki özelliklere sahiptir:

- Arabirimdeki her yöntem belirli bir hizmet işlemine karşılık gelir. 
- Her arabirim için <xref:System.ServiceModel.ServiceContractAttribute> özniteliğini uygulamanız gerekir.
- Her işlem/yöntem için <xref:System.ServiceModel.OperationContractAttribute> özniteliğini uygulamanız gerekir. 

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> - Bir **WCF hizmet kitaplığı** projesi oluşturun.
> - Bir hizmet sözleşmesi arabirimi tanımlayın.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Bir WCF hizmet kitaplığı projesi oluşturma ve bir hizmet sözleşmesi arabirimi tanımlama

1. Visual Studio 'Yu yönetici olarak açın. Bunu yapmak için **Başlat** menüsünde Visual Studio programını seçin ve ardından kısayol menüsünde **yönetici olarak çalıştır** > **daha fazla** ' yı seçin.

2. Bir **WCF hizmet kitaplığı** projesi oluşturun.

   1. Gelen **dosya** menüsünde **yeni** > **proje**.

   2. **Yeni proje** iletişim kutusunda, sol tarafta,  **C# Visual** veya **Visual Basic**' i genişletin ve ardından **WCF** kategorisini seçin. Visual Studio, pencerenin orta bölümündeki proje şablonlarının bir listesini görüntüler. **WCF hizmet kitaplığı**' nı seçin.

      > [!NOTE]
      > **WCF** proje şablonu kategorisini görmüyorsanız, Visual Studio 'nun **Windows Communication Foundation** bileşenini yüklemeniz gerekebilir. **Yeni proje** iletişim kutusunda, sol taraftaki **Visual Studio yükleyicisi aç** bağlantısını seçin. **Ayrı bileşenler** sekmesini seçin ve ardından **geliştirme etkinlikleri** kategorisinin **Windows Communication Foundation** bulun ve seçin. Bileşeni yüklemeye başlamak için **Değiştir** ' i seçin.

   3. Pencerenin alt bölümünde, **ad** Için *GettingStartedLib* ve **çözüm adı**olarak *gettingstarted* girin. 

   4. Seçin **Tamam**.

      Visual Studio, üç dosya içeren projeyi oluşturur: *IService1.cs* (veya *IService1. vb.* Visual Basic projesi için), *Service1.cs* (veya *Service1. Visual Basic vb* ) ve *app. config*. Visual Studio bu dosyaları aşağıdaki gibi tanımlar: 
      - *IService1* dosyası, hizmet sözleşmesinin varsayılan tanımını içerir. 
      - *Service1* dosyası, hizmet sözleşmesinin varsayılan uygulamasını içerir. 
      - *App. config* dosyası, VISUAL Studio WCF hizmeti ana bilgisayar aracı ile varsayılan hizmeti yüklemek için gereken yapılandırma bilgilerini içerir. WCF hizmeti ana bilgisayar aracı hakkında daha fazla bilgi için bkz. [WCF hizmet Konağı (WcfSvcHost. exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Visual Studio 'Yu Visual Basic Geliştirici ortamı ayarları ile yüklediyseniz, çözüm gizlenmiş olabilir. Bu durumda, **Araçlar** menüsünden **Seçenekler** ' i seçin ve ardından **seçenekler** penceresinde **Projeler ve çözümler** ** > '** ni seçin. **Çözümü her zaman göster**' i seçin. Ayrıca, **oluşturulduğunda yeni projeleri kaydet** ' in seçili olduğunu doğrulayın.

3. **Çözüm Gezgini**, **IService1.cs** veya **IService1. vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:

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

     Bu sözleşme, çevrimiçi bir Hesaplayıcı tanımlar. `ICalculator` arabiriminin <xref:System.ServiceModel.ServiceContractAttribute> özniteliğiyle (Basitleştirilmiş `ServiceContract`olarak) işaretlendiğini görürsünüz. Bu öznitelik, anlaşma adının belirsizliğini ortadan kaldırmak için bir ad alanını tanımlar. Kod, her Hesaplayıcı işlemini <xref:System.ServiceModel.OperationContractAttribute> özniteliğiyle işaretler (`OperationContract`olarak basitleştik).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Bir WCF hizmet kitaplığı projesi oluşturun.
> - Bir hizmet sözleşmesi arabirimi tanımlayın.

WCF hizmeti sözleşmesinin nasıl uygulanacağını öğrenmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: WCF hizmet sözleşmesi uygulama](how-to-implement-a-wcf-contract.md)
