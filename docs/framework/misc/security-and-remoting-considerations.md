---
title: Güvenlik ve Uzaktan Yönetim Konuları
ms.date: 03/30/2017
helpviewer_keywords:
- code security, remoting
- remoting, security
- security [.NET Framework], remoting
- secure coding, remoting
ms.assetid: 125d2ab8-55a4-4e5f-af36-a7d401a37ab0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db4a5ee5673ef96c9fb7f39798ab32dd8c910f43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398176"
---
# <a name="security-and-remoting-considerations"></a>Güvenlik ve Uzaktan Yönetim Konuları
Remoting uygulama etki alanları, işlemler veya bilgisayarlar arasında çağırma saydam ayarlamanıza olanak sağlar. Bununla birlikte, kod erişim güvenliği yığın İlerlemesi (aynı işlem uygulama etki alanları arasında geçerli) işlem veya makine sınırları çapraz olamaz.  
  
 Uzaktan erişilebilir herhangi bir sınıf (türetilmiş bir <xref:System.MarshalByRefObject> sınıfı) güvenlik sorumluluğunu yapması gerekmez. Ya da kapalı ortamlarda yalnızca burada çağıran kodu örtük olarak güvenilir olabilir veya böylece bunlar korumalı kod kötü amaçlı olarak kullanılabilecek dış girişe edilmez remoting çağrıları tasarlanmalıdır kodu kullanılmalıdır.  
  
 Genellikle, hiçbir zaman yöntemler, özellikler veya bildirim temelli tarafından korunan olayları açığa [LinkDemand](../../../docs/framework/misc/link-demands.md) ve <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> güvenlik denetimleri. Remoting ile bu denetimleri zorunlu değildir. Gibi diğer güvenlik denetimlerini <xref:System.Security.Permissions.SecurityAction.Demand>, [Assert](../../../docs/framework/misc/using-the-assert-method.md)ve benzeri bir işlem içinde uygulama etki alanları arasında çalışır ancak işlem içi veya makineler arası senaryolarda çalışmaz.  
  
## <a name="protected-objects"></a>Korunan nesneler  
 Bazı nesneler kendilerini güvenlik durumda tutun. Bu nesneler, sonra güvenlik yetkilendirme kendi izinlerini ötesinde almak güvenilmeyen koduna geçirilmemelidir.  
  
 Bir örnek oluştururken bir <xref:System.IO.FileStream> nesnesi. <xref:System.Security.Permissions.FileIOPermission> Oluşturma sırasında talep ve başarılı olursa, dosya nesnesi döndürülür. Ancak, bu nesne başvurusu kodu dosya izinleri olmadan geçirilir, nesne okuyabilmesini ve bu belirli bir dosyaya yazma olacaktır.  
  
 Böyle bir nesnenin en basit savunma aynı talep vermektir **FileIOPermission** nesne başvurusu bir ortak API öğesi aracılığıyla almak için arama kod.  
  
## <a name="application-domain-crossing-issues"></a>Uygulama etki alanı aşma sorunları  
 Yönetilen barındırma ortamları kodda yalıtmak için çeşitli derlemeler için izin düzeylerinin azaltma açık ilkesiyle birden çok alt uygulama etki alanları oluşturmak için yaygındır. Ancak, varsayılan uygulama etki alanında bu derlemeler için ilke değişmeden kalır. Bir alt uygulama etki alanlarının bir derlemeyi yüklemeye varsayılan uygulama etki alanı zorlayabilirsiniz, kod yalıtım etkisini kaybolur ve zorla yüklenen derlemesindeki türler güven daha yüksek bir düzeyde kod çalıştırabilir.  
  
 Uygulama etki alanı, burada bir uygulama etki alanında barındırılan bir nesne için bir proxy çağırarak yer alan kod bir derlemeyi yüklemek ve çalıştırmak için başka bir uygulama etki alanı zorlayabilirsiniz. Uygulama etki alanları arası proxy edinmek için nesneyi barındıran uygulama etki alanı aracılığıyla bir yöntem çağrısı parametresi ya da döndürme değeri dağıtmanız gerekir. Veya, uygulama etki alanı yalnızca oluşturulduysa oluşturan bir proxy <xref:System.AppDomain> varsayılan nesne. Bu nedenle, kod yalıtım çiğnemekten kaçının, daha yüksek bir güven düzeyi içeren bir uygulama etki alanı sıralanmış-by-reference nesnelerin referansları dağıtmanız değil (sınıfların örneklerini türetilen <xref:System.MarshalByRefObject>) alt ile uygulama etki alanları için kendi etki alanındaki güven düzeyleri.  
  
 Genellikle, varsayılan uygulama etki alanı her biri bir denetim nesnesiyle uygulama etki alanları alt oluşturur. Denetim nesnesi yeni uygulama etki alanı yönetir ve bazen siparişleri varsayılan uygulama etki alanından alır, ancak bunu gerçekten etki alanı doğrudan bağlanamazsınız. Bazen, varsayılan uygulama etki alanı kendi proxy denetim nesnesi ile çağırır. Ancak, varsayılan uygulama etki alanına geri çağırmaya denetim nesnesi için gerekli olduğu durumlar olabilir. Bu durumda, varsayılan uygulama etki alanı denetim nesnesi oluşturucuya başvuruya göre geri çağırma nesnesi geçirir. Bu proxy korumak için denetim nesnesi sorumluluğundadır. Denetim nesnesi proxy bir ortak statik ortak sınıfının alana veya aksi halde proxy genel olarak kullanıma olsaydı, bu varsayılan uygulama etki alanına geri aramayı başka bir kod tehlikeli olabilecek bir mekanizma açılacaktır. Bu nedenle, Denetim nesneler her zaman proxy gizliliğini korumak için örtük olarak güvenilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
