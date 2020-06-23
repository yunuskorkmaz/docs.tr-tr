---
title: 'Öğretici: Windows Communication Foundation hizmet sözleşmesi tanımlama'
description: Bir WCF uygulaması oluşturmaya başlamanıza yardımcı olan bir makale serisinin parçası olarak bir hizmet sözleşmesini nasıl tanımlayacağınızı öğrenin.
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 5cb371da8c7180b8c4cbf5ac11468fbb8e0e13cc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246317"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Öğretici: Windows Communication Foundation hizmet sözleşmesi tanımlama

Bu öğreticide, temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevden ilki açıklanmaktadır. Öğreticilere genel bakış için bkz. [öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).

Bir WCF hizmeti oluşturduğunuzda, ilk göreviniz bir hizmet sözleşmesini tanımlamaktır. Hizmet sözleşmesi, hizmetin desteklediği işlemleri belirtir. Bir işlem, bir Web hizmeti yöntemi olarak düşünülebilir. Bir C# veya Visual Basic arabirimi tanımlayarak hizmet sözleşmeleri oluşturursunuz. Bir arabirim aşağıdaki özelliklere sahiptir:

- Arabirimdeki her yöntem belirli bir hizmet işlemine karşılık gelir.
- Her arabirim için özniteliği uygulamanız gerekir <xref:System.ServiceModel.ServiceContractAttribute> .
- Her işlem/yöntem için özniteliği uygulamanız gerekir <xref:System.ServiceModel.OperationContractAttribute> .

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:
> [!div class="checklist"]
>
> - Bir **WCF hizmet kitaplığı** projesi oluşturun.
> - Bir hizmet sözleşmesi arabirimi tanımlayın.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Bir WCF hizmet kitaplığı projesi oluşturma ve bir hizmet sözleşmesi arabirimi tanımlama

1. Visual Studio 'Yu yönetici olarak açın. Bunu yapmak için **Başlat** menüsünde Visual Studio **programını seçin ve**ardından  >  kısayol menüsünde**yönetici olarak çalıştır** ' ı seçin.

2. Bir **WCF hizmet kitaplığı** projesi oluşturun.

   1. **Dosya** menüsünden **Yeni**  >  **Proje**' yi seçin.

   2. **Yeni proje** iletişim kutusunda, sol taraftaki **Visual C#** veya **Visual Basic**öğesini genişletin ve ardından **WCF** kategorisini seçin. Visual Studio, pencerenin orta bölümündeki proje şablonlarının bir listesini görüntüler. **WCF hizmet kitaplığı**' nı seçin.

      > [!NOTE]
      > **WCF** proje şablonu kategorisini görmüyorsanız, Visual Studio 'nun **Windows Communication Foundation** bileşenini yüklemeniz gerekebilir. **Yeni proje** iletişim kutusunda, sol taraftaki **Visual Studio yükleyicisi aç** bağlantısını seçin. **Ayrı bileşenler** sekmesini seçin ve ardından **geliştirme etkinlikleri** kategorisinin **Windows Communication Foundation** bulun ve seçin. Bileşeni yüklemeye başlamak için **Değiştir** ' i seçin.

   3. Pencerenin alt bölümünde, **ad** Için *GettingStartedLib* ve **çözüm adı**olarak *gettingstarted* girin.

   4. **Tamam**’ı seçin.

      Visual Studio, üç dosya içeren projeyi oluşturur: *IService1.cs* (veya *IService1. vb.* Visual Basic projesi için), *Service1.cs* (veya *Service1. Visual Basic vb* ) ve *App.config*. Visual Studio bu dosyaları aşağıdaki gibi tanımlar:
      - *IService1* dosyası, hizmet sözleşmesinin varsayılan tanımını içerir.
      - *Service1* dosyası, hizmet sözleşmesinin varsayılan uygulamasını içerir.
      - *App.config* dosyası, VISUAL Studio WCF hizmeti ana bilgisayar aracı ile varsayılan hizmeti yüklemek için gereken yapılandırma bilgilerini içerir. WCF hizmeti ana bilgisayar aracı hakkında daha fazla bilgi için bkz. [WCF hizmet Konağı (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Visual Studio 'Yu Visual Basic Geliştirici ortamı ayarları ile yüklediyseniz, çözüm gizlenmiş olabilir. Bu durumda, **Araçlar** menüsünden **Seçenekler** ' i seçin ve ardından Seçenekler penceresinde **Projeler ve çözümler**  >  **genel** ' i seçin. **Options** **Çözümü her zaman göster**' i seçin. Ayrıca, **oluşturulduğunda yeni projeleri kaydet** ' in seçili olduğunu doğrulayın.

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

     Bu sözleşme, çevrimiçi bir Hesaplayıcı tanımlar. `ICalculator`Arabirimin <xref:System.ServiceModel.ServiceContractAttribute> özniteliğiyle (Basitleştirilmiş olarak) işaretlendiğini görürsünüz `ServiceContract` . Bu öznitelik, anlaşma adının belirsizliğini ortadan kaldırmak için bir ad alanını tanımlar. Kod, her Hesaplayıcı işlemini <xref:System.ServiceModel.OperationContractAttribute> özniteliğiyle (Basitleştirilmiş olarak) işaretler `OperationContract` .

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Bir WCF hizmet kitaplığı projesi oluşturun.
> - Bir hizmet sözleşmesi arabirimi tanımlayın.

WCF hizmeti sözleşmesinin nasıl uygulanacağını öğrenmek için bir sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Öğretici: WCF hizmet sözleşmesi uygulama](how-to-implement-a-wcf-contract.md)
