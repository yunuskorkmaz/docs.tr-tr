---
title: 'Nasıl yapılır: Windows Communication Foundation Hizmet Sözleşmesini Tanımlama'
ms.date: 09/14/2018
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 9f7f696b1f5be2e96c50938f4627271d891deb32
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582206"
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a>Nasıl yapılır: Windows Communication Foundation Hizmet Sözleşmesini Tanımlama
İlk altı görev temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken budur. Tüm altı görevleri genel bakış için bkz. [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.

 Bir WCF Hizmeti oluştururken, ilk görev bir hizmet sözleşmesini tanımlamaktır. Hizmet sözleşmesi hangi işlemleri belirtir destekler. Bir işlem, bir Web hizmeti yöntemi düşünülebilir. Sözleşmeler, bir C++, C# veya Visual Basic (VB) arabirimi tanımlamasıyla oluşturulur. Arabirimdeki her yöntem için bir hizmet işlemiyle karşılık gelir. Her arabirimde <xref:System.ServiceModel.ServiceContractAttribute> uygulanan ve her bir işlem olmalıdır <xref:System.ServiceModel.OperationContractAttribute> özniteliğinin. Arabirimdeki bir yöntem mümkünse <xref:System.ServiceModel.ServiceContractAttribute> özniteliği yok <xref:System.ServiceModel.OperationContractAttribute> öznitelik, hizmet tarafından yöntemi gösterilmez.

 Bu görev için kullanılan kod, aşağıdaki yordamın örnekte sağlanır.

## <a name="define-a-service-contract"></a>Bir hizmet sözleşmesini tanımlama

1. Visual Studio'yu yönetici olarak açın programa sağ tıklayarak **Başlat** menü ve seçerek **daha fazla** > **yönetici olarak çalıştır**.

2. Bir WCF hizmet kitaplığı projesi oluşturun.

   1. Gelen **dosya** menüsünde **yeni** > **proje**.

   2. İçinde **yeni proje** iletişim kutusunda sol taraftaki genişletin **Visual C#** veya **Visual Basic**ve ardından **WCF** kategorisi. Proje şablonları listesi, iletişim kutusunun merkez bölümünde görüntülenir. Seçin **WCF hizmet Kitaplığı**.

   3. Girin `GettingStartedLib` içinde **adı** metin kutusu ve `GettingStarted` içinde **çözüm adı** iletişim kutusunun altındaki metin.

   > [!NOTE]
   > Görmüyorsanız **WCF** proje şablonu kategorisi yüklemeniz gerekebilir **Windows Communication Foundation** Visual Studio bileşen. İçinde **yeni proje** iletişim kutusunda, bağlantısına **açık Visual Studio yükleyicisi**. Seçin **tek tek bileşenler** sekmesine ve ardından bulmak ve seçmek **Windows Communication Foundation** altında **geliştirme etkinliklerini** kategorisi. Seçin **Değiştir** bileşeni yüklemeyi başlatmak için.

   Visual Studio 3 dosyaları içeren projeyi oluşturur: Iservice1.cs (veya Iservice1.vb) Service1.cs (veya gt;service1.vb) ve App.config. Varsayılan hizmet sözleşmesini Iservice1 dosya içerir. Varsayılan bir uygulama hizmet sözleşmesinin Service1 dosya içerir. App.config dosyasını Visual Studio WCF hizmet konağı varsayılan hizmetiyle yüklemek için gerekli yapılandırmayı içerir. WCF hizmet konağı aracı hakkında daha fazla bilgi için bkz. [WCF hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)

3. Iservice1.cs veya Iservice1.vb dosyasını açın ve ad alanı bildirimi bırakarak ad alanı bildirimi içindeki kod silin. Ad alanı içinde bildirimi adlı yeni arabirimi tanımlayın `ICalculator` aşağıdaki kodda gösterildiği gibi.

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

     Bu sözleşme, çevrimiçi bir hesap makinesi tanımlar. Bildirim `ICalculator` arabirimi ile işaretlenmiş <xref:System.ServiceModel.ServiceContractAttribute> özniteliği. Bu öznitelik sözleşme adı ayırt etmek için kullanılan bir ad alanı tanımlar. Her hesap makinesi işlemi ile işaretlenmiş <xref:System.ServiceModel.OperationContractAttribute> özniteliği.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Nasıl yapılır: bir hizmet sözleşmesini uygulama](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Nasıl yapılır: Bir Hizmet Anlaşmasını Uygulama](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [Başlarken](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Kendini Barındırma](../../../docs/framework/wcf/samples/self-host.md)