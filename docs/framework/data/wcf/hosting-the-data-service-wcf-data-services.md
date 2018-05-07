---
title: Veri Hizmeti (WCF Veri Hizmetleri) barındırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: d3adf45e0876ae63b111a53461eee9aeee519b5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-the-data-service-wcf-data-services"></a>Veri Hizmeti (WCF Veri Hizmetleri) barındırma
Kullanarak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], olarak kullanıma sunan bir hizmet oluşturabilmeniz için bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış. Bu veri hizmeti öğesinden devralınan bir sınıf olarak tanımlanır <xref:System.Data.Services.DataService%601>. Bu sınıf, istek iletilerini işlemek, veri kaynağına karşı güncelleştirmeleri gerçekleştirmek ve gerektirdiği şekilde yanıt iletileri oluşturmak için gereken işlevleri sağlar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Ancak, bir veri hizmeti bağlamak ve ağ yuvada gelen HTTP isteklerini dinlemeye. Bu gerekli işlevselliği için bir barındırma bileşenin veri hizmeti kullanır.  
  
 Veri Hizmeti ana veri hizmeti adına aşağıdaki görevleri gerçekleştirir:  
  
-   İsteklerini dinler ve bu istekleri için veri hizmeti yönlendirir.  
  
-   Her istek için veri hizmeti örneğini oluşturur.  
  
-   Veri Hizmeti gelen istek işlemi istek sayısı.  
  
-   Veri hizmeti adına yanıt gönderir.  
  
 Veri hizmetini barındıran basitleştirmek için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Windows Communication Foundation (WCF) ile tümleştirmek için tasarlanmıştır. Veri Hizmeti veri hizmeti konak görevi gören bir varsayılan WCF uygulaması sağlayan bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama. Bu nedenle, bir veri hizmeti aşağıdaki yollardan biriyle barındırabilir:  
  
-   İçinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.  
  
-   Kendini barındıran WCF hizmetlerini destekleyen yönetilen bir uygulamada.  
  
-   Bazı diğer özel veri hizmeti ana bilgisayarı.  
  
## <a name="hosting-a-data-service-in-an-aspnet-application"></a>Bir ASP.NET uygulamasında veri hizmeti barındırma  
 Kullandığınızda **Yeni Öğe Ekle** iletişim aracı bir ASP.NET uygulamasındaki bir veri hizmeti tanımlamak için Visual Studio'da projeye iki yeni dosyaları oluşturur. İlk dosya sahip bir `.svc` uzantısı ve veri hizmeti örneği oluşturmak nasıl WCF çalışma zamanı bildirir. Aşağıdaki tamamladığınızda oluşturduğunuz Northwind örnek veri hizmeti bu dosyayı örneğidir [Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):  
  
```  
<%@ ServiceHost Language="C#"   
    Factory="System.Data.Services.DataServiceHostFactory,   
            System.Data.Services, Version=4.0.0.0,   
            Culture=neutral, PublicKeyToken=b77a5c561934e089"   
    Service="NorthwindService.Northwind" %>   
```  
  
 Bu yönerge kullanarak hizmet ana bilgisayarı adlandırılmış veri hizmet sınıfı oluşturmak için uygulama söyler <xref:System.Data.Services.DataServiceHostFactory> sınıfı.  
  
 Arka plan kodu sayfada `.svc` dosya şu şekilde Northwind örnek veri hizmeti için tanımlanan veri hizmetin kendisini uygulamasıdır sınıfı içerir:  
  
 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
 Veri hizmeti bir WCF hizmeti gibi davrandığı için veri hizmeti ile tümleştirilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve WCF Web programlama modelini izler. Daha fazla bilgi için bkz: [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) ve [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).  
  
## <a name="self-hosted-wcf-services"></a>Kendini barındıran WCF hizmetleri  
 WCF uygulaması sahiptir çünkü [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] veri hizmeti bir WCF hizmeti olarak kendi kendine barındırma destekler. Bir hizmet birinde kendini barındıran [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bir konsol uygulaması gibi uygulama. <xref:System.Data.Services.DataServiceHost> Devraldığı sınıfı <xref:System.ServiceModel.Web.WebServiceHost>, belirli bir adresinden veri hizmeti örneğini oluşturmak için kullanılır.  
  
 Bu, dağıtmayı ve hizmet sorunlarını kolaylaştırabilir çünkü kendi kendine barındırma geliştirme ve test amacıyla kullanılabilir. Ancak, bu tür barındırma tarafından sağlanan Gelişmiş barındırma ve yönetim özellikleri sağlamaz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] veya Internet Information Services (IIS) tarafından. Daha fazla bilgi için bkz: [yönetilen bir uygulamada barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).  
  
## <a name="defining-a-custom-data-service-host"></a>Bir özel veri hizmeti ana bilgisayarı tanımlama  
 WCF konak uygulaması çok kısıtlayıcı olduğu durumlarda, özel bir ana bilgisayar veri hizmeti için de tanımlayabilirsiniz. Uygulayan herhangi bir sınıf <xref:System.Data.Services.IDataServiceHost> arabirimi kullanılabilir ağ ana bilgisayar için bir veri hizmeti. Özel bir ana bilgisayar uygulamalıdır <xref:System.Data.Services.IDataServiceHost> arabirim ve veri hizmeti ana bilgisayarı aşağıdaki temel sorumluluklarını işleyebilen:  
  
-   Veri Hizmeti ile hizmet kök yolu sağlar.  
  
-   İşlem istek ve yanıt üstbilgileri bilgi uygun <xref:System.Data.Services.IDataServiceHost> üye uygulama.  
  
-   Veri Hizmeti tarafından oluşturulan özel durumları işleme.  
  
-   Sorgu dizesi parametreleri doğrulayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Verilerinizi Hizmet Olarak Kullanıma Sunma](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)  
 [Veri Hizmeti Yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
