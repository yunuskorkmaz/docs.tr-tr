---
title: 'Nasıl yapılır: Windows Communication Foundation Hizmet Sözleşmesini Tanımlama'
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], defining
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 98e0b07f608db4396a5b8f5e25cde243e03390a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a>Nasıl yapılır: Windows Communication Foundation Hizmet Sözleşmesini Tanımlama
Temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken altı görevler ilk budur. Tüm altı görevlerinin genel bakış için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.  
  
 Oluştururken bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti, ilk görev, bir hizmet sözleşmesini tanımlamak için. Hizmet sözleşmesi hangi işlemleri belirtir hizmet destekler. Bir işlem, bir Web hizmeti yöntemi düşünülebilir. Sözleşmeler, C++, C# veya Visual Basic (VB) arabirimi tanımlamasıyla oluşturulur. Arabirimdeki her yöntem belirli hizmet işlemine karşılık gelir. Her arabirimde <xref:System.ServiceModel.ServiceContractAttribute> uygulanan ve her işlem olmalıdır <xref:System.ServiceModel.OperationContractAttribute> özniteliğinin. Bir yöntemi varsa içeren bir arabirim içinde <xref:System.ServiceModel.ServiceContractAttribute> özniteliği yok <xref:System.ServiceModel.OperationContractAttribute> özniteliği yöntemi hizmeti tarafından gösterilmez.  
  
 Bu görev için kullanılan kod, aşağıdaki yordamın örnekte sağlanır.  
  
### <a name="to-define-a-service-contract"></a>Bir hizmet sözleşmesini tanımlamak için  
  
1.  Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] programa sağ tarafından yönetici olarak **Başlat** menü ve seçerek **yönetici olarak çalıştır**.  
  
2.  Tıklayarak bir WCF Hizmeti kitaplığı projesi oluşturma **dosya** menü ve seçerek **yeni**, **proje**. İçinde **yeni proje** iletişim kutusunda, iletişim kutusunun sol tarafında genişletin **Visual C#** bir C# projesi için veya **diğer diller** ve ardından **Visual Basic** Visual Basic projesinde için. Seçili dili altında seçin **WCF** ve proje şablonları listesini iletişim merkezi bölümünde görüntülenir. Seçin **WCF Hizmeti Kitaplığı**ve türü `GettingStartedLib` içinde **adı** textbox ve `GettingStarted` içinde **çözüm adı** iletişim kutusunun altındaki metin kutusuna.  
  
3.  Visual Studio 3 dosyaları içeren proje oluşturma: IService1.cs (veya IService1.vb) service1.cs dosyasını (veya Service1.vb) ve App.config.  Varsayılan hizmet sözleşmesini IService1 dosyası içerir.  Service1 dosyayı varsayılan uygulama hizmet sözleşmesinin içerir. App.config dosyasını Visual Studio WCF hizmet konağı varsayılan hizmetiyle yüklemek için gerekli yapılandırmayı içerir. WCF hizmet konağı aracı hakkında daha fazla bilgi için bkz: [WCF hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
4.  IService1.cs veya IService1.vb dosyasını açın ve ad alanı bildirimi bırakarak ad alanı bildiriminin içindeki kod silin. İçinde ad alanı bildirimi tanımlamak adlı yeni bir arabirim `ICalculator` aşağıdaki kodda gösterildiği gibi.  
  
    ```  
    // IService.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
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
  
    ```  
    ‘IService.vb  
    Imports System  
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
  
     Bu sözleşme çevrimiçi hesaplayıcı tanımlar. Bildirim `ICalculator` arabirimi ile işaretlenmiş <xref:System.ServiceModel.ServiceContractAttribute> özniteliği. Bu öznitelik sözleşme adı ayırt etmek için kullanılan bir ad alanını tanımlar. Her hesap makinesi işlemi ile işaretlenmiş <xref:System.ServiceModel.OperationContractAttribute> özniteliği.  
  
    > [!NOTE]
    >  Bir arabirim, üye veya sınıf ek açıklama eklemek için öznitelikleri kullanma, öznitelik adı "Özniteliği" bölümü düşürebilir. Bu nedenle <xref:System.ServiceModel.ServiceContractAttribute> hale `[ServiceContract]` C# veya `<ServiceContract>` Visual Basic'te.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Nasıl yapılır: Bir Hizmet Anlaşmasını Uygulama](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [Başlarken](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Kendini Barındırma](../../../docs/framework/wcf/samples/self-host.md)
