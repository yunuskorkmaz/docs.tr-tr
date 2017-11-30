---
title: "Derleme Bağlama Yönlendirmesi Güvenlik İzni"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ddaf9965a3b3b5d6171a643b198db93309afad48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-binding-redirection-security-permission"></a>Derleme Bağlama Yönlendirmesi Güvenlik İzni
Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir. Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir. Ayarlayarak iznine sahip <xref:System.Security.Permissions.SecurityPermissionFlag> üzerinde bayrak <xref:System.Security.Permissions.SecurityPermission>. Yönetilen derlemeler varsayılan olarak bir izniniz yok.  
  
 Intranet bölgesi ve Güvenilen Bölge (yerel makine) içinde çalışan uygulamalar için güvenlik izni verilir. Internet bölgesinde çalışan uygulamalar Derleme bağlaması yeniden yönlendirme gerçekleştiren kesinlikle yasaktır.  
  
 Derleme yeniden yönlendirme bileşen yayımcı tarafından denetlenen bir yayımcı ilkesi dosyası ya da yönetici tarafından denetlenen makine yapılandırma dosyası gerçekleştirdiyseniz izni gerekli değildir. Ancak, bir uygulama ilkesi publisher'ı kullanarak açıkça yoksaymak izni gereklidir [ \<publisherPolicy uygulamak = "Hayır" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) uygulama yapılandırma dosyasında öğesi.  
  
 Varsayılan güvenlik ayarlarını aşağıdaki tabloda gösterilmektedir **BindingRedirects** bayrağı.  
  
|Bölge|BindingRedirects bayrağı ayarlama|  
|----------|-----------------------------------|  
|Güvenilir bölgeye (yerel makine)|**AÇIK**|  
|İntranet bölgesi|**AÇIK**|  
|Internet Bölgesi|**KAPALI**|  
|Güvenilmeyen bölgeleri|**KAPALI**|  
  
 Bir yönetici veya kısıtlama verilen bir bilgisayardaki belirli senaryoları desteklemek üzere bu güvenlik ayarlarını değiştirebilirsiniz. Değiştirmek için hiçbir araç vardır **BindingRedirects** varsayılandan; ayarlama bayrağı yönetici el ile bir kullanıcının bilgisayarda Security.config dosyasını düzenlemeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yayımcı ilke dosyaları ve yan yana yürütme](http://msdn.microsoft.com/en-us/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [Nasıl yapılır: etkinleştirme ve otomatik bağlama yönlendirmesini devre dışı](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [Yan yana yürütme](../../../docs/framework/deployment/side-by-side-execution.md)
