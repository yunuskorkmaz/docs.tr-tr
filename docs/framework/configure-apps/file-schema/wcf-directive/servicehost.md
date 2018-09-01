---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 730b1188a95d0e35d7431d43884e867e5520585e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396411"
---
# <a name="servicehost"></a>\@ServiceHost
Barındırılan hizmet konak hizmeti ile üretmek için kullanılan Üreteç ve erişmek veya .svc dosyasında sağlanan barındırma Kodu derlemek için gereken diğer programlama özelliklerini ilişkilendirir.  
  
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
 Barındırılan hizmet CLR türü adı. Bu, bir veya daha fazla hizmet kişileri uygulayan bir tür tam bir adı olmalıdır.  
  
#### <a name="factory"></a>Fabrika  
 Hizmet ana bilgisayarı örneği oluşturmak için kullanılan hizmet barındırma ortamı fabrikası CLR türü adı. Bu öznitelik isteğe bağlıdır. Belirtilmemişse, varsayılan <xref:System.ServiceModel.Activation.ServiceHostFactory> kullanılan örneğini döndüren <xref:System.ServiceModel.ServiceHost>.  
  
#### <a name="debug"></a>Hata ayıklama  
 Windows Communication Foundation (WCF) hizmet hata ayıklama sembolleriyle derlenmiş olup olmadığını gösterir. `true` WCF hizmet hata ayıklama sembolleriyle derlenmiş Aksi takdirde, `false`.  
  
#### <a name="language"></a>Dil  
 Dosya (.svc) içindeki tüm satır içi kod derlenirken kullanılan dili belirtir. Değerlerin herhangi temsil edebilir. C#, VB ve C#, Visual Basic .NET ve JScript .NET için sırasıyla başvuran JS dahil olmak üzere ağ tarafından desteklenen dil. Bu öznitelik isteğe bağlıdır.  
  
#### <a name="codebehind"></a>CodeBehind  
 XML Web hizmeti XML Web hizmeti uygulayan sınıfı aynı dosyada bulunmadığı ve edilmemiş bir bütünleştirilmiş kod içine derlenmiş ve \Bin dizinine olduğunda uygulayan kaynak dosyasını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.ServiceModel.ServiceHost> Hizmeti barındırmak için kullanılan bir Windows Communication Foundation (WCF) programlama modeli içinde genişletilebilirlik noktasıdır. Fabrika düzeni örneği oluşturmak için kullanılan <xref:System.ServiceModel.ServiceHost> , büyük olasılıkla barındırma ortamı doğrudan örneğini oluşturmalıdır değil polimorfik bir tür olduğundan.  
  
 Varsayılan uygulama kullanan <xref:System.ServiceModel.Activation.ServiceHostFactory> bir örneğini oluşturmak için <xref:System.ServiceModel.ServiceHost>. Ancak, Fabrika uygulamanızda CLR tür adını belirterek kendi Fabrika (bir türetilmiş ana döndürür) sağlayabilirsiniz [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi.  
  
 Kendi özel hizmet barındırma ortamı fabrikası yerine varsayılan fabrika kullanmak için yalnızca tür adı sağlayın [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi aşağıdaki gibi:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Fabrika uygulamaları olabildiğince hafif tutun. Özel mantığı çok sayıda varsa, kod içinde yerine ana Fabrika içinde bu mantığı koyarsanız daha yeniden kullanılabilir.  
  
 Örneğin, için AJAX etkinleştirilmiş uç noktayı etkinleştirme `MyService`, belirtin <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> değerini `Factory` varsayılan yerine bir öznitelik <xref:System.ServiceModel.Activation.ServiceHostFactory>, [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönerge olarak Aşağıdaki örnekte gösterilir.  
  
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
