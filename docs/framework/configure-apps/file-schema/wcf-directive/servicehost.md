---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 5498c300ab126bbc4e08cd228e3e7b48e905932e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="servicehost"></a>@ServiceHost
Barındırılacak şekilde hizmet ana bilgisayar hizmeti ile üretmek için kullanılan Üreteç ve erişim veya .svc dosyasında sağlanan barındırma Kodu derlemek için gereken diğer programlama özelliklerini ilişkilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a>Öznitelikler  
  
#### <a name="service"></a>Hizmet  
 Barındırılan hizmete CLR türü adı. Bu, bir veya daha fazla hizmet kişileri uygulayan bir tür tam bir adı olmalıdır.  
  
#### <a name="factory"></a>Fabrika  
 Hizmet ana bilgisayarı örneği oluşturmak için kullanılan hizmet ana bilgisayar üreteci CLR türü adı. Bu öznitelik isteğe bağlıdır. Belirtilmezse, varsayılan <xref:System.ServiceModel.Activation.ServiceHostFactory> kullanılan örneğini döndüren <xref:System.ServiceModel.ServiceHost>.  
  
#### <a name="debug"></a>Hata ayıklama  
 Windows Communication Foundation (WCF) hizmetini hata ayıklama sembolleriyle derlenip derlenmeyeceğini gösterir. `true` WCF Hizmeti hata ayıklama sembolleriyle derlenip Aksi takdirde `false`.  
  
#### <a name="language"></a>Dil  
 Dosya (.svc) içindeki tüm satır içi kod derleme sırasında kullanılan dili belirtir. Değerler herhangi temsil edebilir. C#, VB ve C#, Visual Basic .NET ve JScript .NET sırasıyla başvuru JS içeren NET desteklenen dili. Bu öznitelik isteğe bağlıdır.  
  
#### <a name="codebehind"></a>Arkasındaki koda  
 XML Web hizmeti uygulayan sınıf aynı dosyada bulunmuyor ve edilmemiş bütünleştirilmiş koda derlenmemiş ve \Bin dizinine yerleştirilen yükleyen XML Web hizmeti uygulayan kaynak dosyasını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.ServiceModel.ServiceHost> Hizmet barındırmak için kullanılan Windows Communication Foundation (WCF) programlama modeli içindeki genişletilebilirlik noktasıdır. Fabrika düzeni örneği oluşturmak için kullanılan <xref:System.ServiceModel.ServiceHost> , büyük olasılıkla barındırma ortamı doğrudan örneği değil çok biçimli bir tür olduğundan.  
  
 Varsayılan uygulama kullanan <xref:System.ServiceModel.Activation.ServiceHostFactory> bir örneğini oluşturmak için <xref:System.ServiceModel.ServiceHost>. Ancak Fabrika uygulamanızda CLR türü adını belirterek kendi Fabrika (bir türetilmiş ana bilgisayarınız döndürür) sağlayabilir [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi.  
  
 Varsayılan fabrika yerine kendi özel hizmet ana bilgisayar üreteci kullanmak için yalnızca ın türü adını belirtin [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) şekilde yönergesi:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Fabrika uygulamaları olabildiğince hafif tutun. Çok sayıda özel mantık varsa, kodunuzu yerine, konak Fabrika içinde içinde bu mantığı yerleştirirseniz daha yeniden kullanılabilir.  
  
 Örneğin, bir AJAX etkinleştirilmiş uç nokta için etkinleştirmek için `MyService`, belirtin <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> değerini `Factory` varsayılan yerine özniteliği <xref:System.ServiceModel.Activation.ServiceHostFactory>, [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) olarak yönergesi Aşağıdaki örnekte gösterilir.  
  
## <a name="example"></a>Örnek  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Hizmet Konağı](../../../../../docs/framework/wcf/samples/custom-service-host.md)
