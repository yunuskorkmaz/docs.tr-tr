---
title: Güvenlik ve Uzaktan Yönetim Konuları
description: Uygulama etki alanları, süreçler veya bilgisayarlar arasında şeffaf çağrı ayarlamanıza olanak tanıyan, uzaktan iletişim ile ilgili güvenlik konuları hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- code security, remoting
- remoting, security
- security [.NET Framework], remoting
- secure coding, remoting
ms.assetid: 125d2ab8-55a4-4e5f-af36-a7d401a37ab0
ms.openlocfilehash: 3a272b2a8f164aad07413a069e68a2146d0df6a7
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855718"
---
# <a name="security-and-remoting-considerations"></a>Güvenlik ve Uzaktan Yönetim Konuları

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Uzaktan iletişim, uygulama etki alanları, süreçler veya bilgisayarlar arasında şeffaf çağrı ayarlamanıza olanak sağlar. Ancak, kod erişimi güvenlik yığını, işleme veya makine sınırları üzerinde olamaz (aynı işlemin uygulama etki alanları arasında geçerlidir).  
  
 Uzaktan erişilebilen herhangi bir sınıfın (bir sınıftan türetilmiş <xref:System.MarshalByRefObject> ) güvenlik için sorumluluğu olması gerekir. Kod, yalnızca çağıran kodun örtük olarak güvendiği kapalı ortamlarda kullanılmalıdır veya korumalı kodu, kötü amaçlı olarak kullanılabilecek bir girdinin dışına çıkarmaması için uzaktan iletişim aramaları tasarlanmalıdır.  
  
 Genellikle, bildirim temelli [bağlantı isteği](link-demands.md) ve güvenlik denetimleri ile korunan yöntemleri, özellikleri veya olayları asla kullanıma sunmamanız gerekir <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> . Remoting ile bu denetimler zorlanmaz. <xref:System.Security.Permissions.SecurityAction.Demand>, [Onaylama](using-the-assert-method.md), vb. gibi diğer güvenlik denetimleri, bir işlem içinde uygulama etki alanları arasında çalışır, ancak çapraz işlem veya çapraz makine senaryolarında çalışmaz.  
  
## <a name="protected-objects"></a>Korumalı nesneler  
 Bazı nesneler güvenlik durumunu kendi başlarına tutar. Bu nesneler güvenilmeyen koda geçirilmemelidir, bu da kendi izinlerinin ötesinde güvenlik yetkilendirmesi elde etmez.  
  
 Bir örnek, bir <xref:System.IO.FileStream> nesne oluşturuyor. , <xref:System.Security.Permissions.FileIOPermission> Oluşturma sırasında talep edilir ve başarılı olursa dosya nesnesi döndürülür. Ancak, bu nesne başvurusu dosya izinleri olmadan koda geçirilirse, nesne bu belirli dosyayı okuyup yazabilir.  
  
 Böyle bir nesne için en basit savunma, bir ortak API öğesi aracılığıyla nesne başvurusunu almak üzere arayan herhangi bir kod için aynı **Dosya** adını talep etmek içindir.  
  
## <a name="application-domain-crossing-issues"></a>Uygulama etki alanı kesişen sorunlar  
 Yönetilen barındırma ortamlarında kodu yalıtmak için, çeşitli derlemeler için izin düzeylerini azaltan açık ilkeyle birden çok alt uygulama etki alanı oluşturmak yaygındır. Ancak, bu derlemelerin ilkesi varsayılan uygulama etki alanında değişmeden kalır. Alt uygulama etki alanlarından biri varsayılan uygulama etki alanını bir derlemeyi yüklemeye zorlabiliyor ise, kod yalıtımının etkisi kaybolur ve zorla yüklenen derlemedeki türler daha yüksek bir güven düzeyinde kod çalıştırabilecektir.  
  
 Bir uygulama etki alanı, başka bir uygulama etki alanının bir derlemeyi yüklemesine ve bir proxy 'yi diğer uygulama etki alanında barındırılan bir nesneye çağırarak içinde yer alan kodu çalıştırmasına zorlayabilir. Çapraz uygulama etki alanı proxy 'si almak için, nesneyi barındıran uygulama etki alanının bir yöntem çağrısı parametresi veya dönüş değeri aracılığıyla bir tane dağıtması gerekir. Ya da uygulama etki alanı yeni oluşturulduysa, oluşturucunun varsayılan olarak nesnesine bir proxy 'si vardır <xref:System.AppDomain> . Bu nedenle, kod yalıtımının kesilmesini önlemek için, daha yüksek bir güven düzeyine sahip bir uygulama etki alanı, <xref:System.MarshalByRefObject> etki alanı içinde, daha düşük güven düzeylerine sahip uygulama etki alanları için sıralanmış başvuru nesnelerine (sınıfından türetilmiş sınıfların örnekleri) başvuruları dağıtmamalıdır.  
  
 Genellikle, varsayılan uygulama etki alanı her birinde bir denetim nesnesi olan alt uygulama etki alanlarını oluşturur. Denetim nesnesi yeni uygulama etki alanını yönetir ve ara sıra varsayılan uygulama etki alanından siparişleri alır, ancak doğrudan etki alanıyla doğrudan bağlantı kuramıyor. Bazen, varsayılan uygulama etki alanı proxy 'sini denetim nesnesine çağırır. Ancak, Denetim nesnesinin varsayılan uygulama etki alanına geri çağırması için gereken durumlar olabilir. Bu durumlarda, varsayılan uygulama etki alanı, Denetim nesnesinin oluşturucusuna başvuruya göre sıralama geri çağırma nesnesi geçirir. Bu proxy 'yi korumak için Denetim nesnesinin sorumluluğundadır. Denetim nesnesi proxy 'yi ortak bir sınıfın ortak statik alanına yerleştirirse veya proxy 'yi herkese açık bir şekilde açıkalıyorsa, diğer kodun varsayılan uygulama etki alanına geri çağırması için tehlikeli bir mekanizma açılır. Bu nedenle, proxy özel tutmak için denetim nesneleri her zaman örtük olarak güvenilirdir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
