---
title: Derleme Bağlama Yönlendirmesi Güvenlik İzni
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: b59689e78f901637674c0a1df28ed74411e8e7c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921382"
---
# <a name="assembly-binding-redirection-security-permission"></a>Derleme Bağlama Yönlendirmesi Güvenlik İzni
Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir. Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir. ' De <xref:System.Security.Permissions.SecurityPermissionFlag> bayrak ayarlanarak izin verilir. <xref:System.Security.Permissions.SecurityPermission> Yönetilen derlemelerin varsayılan olarak izinleri yoktur.  
  
 Güvenlik izni, Güvenilen bölge (yerel makine) ve Intranet bölgesinde çalışan uygulamalara verilir. Internet bölgesinde çalışan uygulamaların, derleme bağlama yeniden yönlendirmesi gerçekleştirmekten kesinlikle izin verilmez.  
  
 Derleme yeniden yönlendirmesi, bileşen yayımcısı tarafından denetlenen bir yayımcı ilke dosyasında ya da yönetici tarafından denetlenen makine yapılandırma dosyasında gerçekleştirilirse, izin gerekli değildir. Ancak, bir uygulamanın uygulama yapılandırma dosyasında [ \<publisherPolicy apply = "No"/>](./file-schema/runtime/publisherpolicy-element.md) öğesini kullanarak yayımcı ilkesini açıkça yoksayması için izin gerekir.  
  
 Aşağıdaki tabloda, **Bindingyönlendirmeler** bayrağıyla ilgili varsayılan güvenlik ayarları gösterilmektedir.  
  
|Bölge|Bindingyönlendirmeler bayrak ayarı|  
|----------|-----------------------------------|  
|Güvenilen bölge (yerel makine)|**DAYANIR**|  
|Intranet bölgesi|**DAYANIR**|  
|Internet Bölgesi|**DIŞINA**|  
|Güvenilmeyen bölgeler|**DIŞINA**|  
  
 Bir yönetici, belirli bir bilgisayardaki belirli senaryoları desteklemek veya kısıtlamak için bu güvenlik ayarlarını değiştirebilir. Varsayılan değer olan **Bindingyönlendirmeler** bayrak ayarını değiştirmek için araç yoktur; bir yönetici, kullanıcının bilgisayarındaki Security. config dosyasını el ile düzenlemeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yayımcı Ilke dosyaları ve yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))
- [Nasıl yapılır: Otomatik bağlama yeniden yönlendirmeyi etkinleştirme ve devre dışı bırakma](how-to-enable-and-disable-automatic-binding-redirection.md)
- [Yan Yana Yürütme](../deployment/side-by-side-execution.md)
