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
ms.openlocfilehash: 46e2e1c327a683782b68069ace2ad6c40bbc856e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868998"
---
# <a name="security-and-remoting-considerations"></a>Güvenlik ve Uzaktan Yönetim Konuları
Uzaktan iletişimini uygulama etki alanları, işlemleri veya bilgisayarlar arasında çağırma saydam ayarlamanıza olanak sağlar. Ancak, kod erişim güvenlik yığın İlerlemesi (aynı işlemde uygulama etki alanları arasında geçerli) işlem veya makine sınırları geçemez.  
  
 Uzaktan erişilebilir herhangi bir sınıf (türetilmiş bir <xref:System.MarshalByRefObject> sınıfı) güvenlik sorumluluğunu yapması gerekmez. Ya da kod kapalı ortamları yalnızca burada çağıran kod örtük olarak güvenilir olabilir veya uzaktan iletişim çağrıları, böylece bunlar korumalı kod kötü amaçla kullanılabilecek dış girişe edilmez tasarlanmalıdır kullanılmalıdır.  
  
 Genellikle, hiçbir zaman yöntemleri, özellikleri ve bildirim temelli tarafından korunan olayları açığa [LinkDemand](../../../docs/framework/misc/link-demands.md) ve <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> güvenlik denetimleri. Uzaktan iletişimi ile bu denetimleri zorunlu değildir. Diğer güvenlik denetimlerini, gibi <xref:System.Security.Permissions.SecurityAction.Demand>, [Assert](../../../docs/framework/misc/using-the-assert-method.md)ve benzeri bir işlem içinde uygulama etki alanları arasında çalışır ancak çapraz işlem veya çapraz makine senaryolarda çalışmaz.  
  
## <a name="protected-objects"></a>Korumalı nesneler  
 Bazı nesneler kendilerini güvenlik durumda tutun. Bu nesneler, ardından kendi izinlerini dışında bir güvenlik yetkilendirmesi sahip olabilir güvenilmeyen koda geçirilmemelidir.  
  
 Bir örnek oluşturduğundan bir <xref:System.IO.FileStream> nesne. <xref:System.Security.Permissions.FileIOPermission> Oluşturma sırasında talep ve başarılı olursa dosya nesne döndürülür. Ancak, bu nesne başvurusu, kod dosya izinleri olmadan aktarılırsa nesne okumak ve bu belirli bir dosyaya yazmak mümkün olacaktır.  
  
 Böyle bir nesne için basit defense aynı talep olmaktır **FileIOPermission** ortak bir API öğesi aracılığıyla nesne başvurusu almak için arayan herhangi bir kod.  
  
## <a name="application-domain-crossing-issues"></a>Uygulama etki alanı kesişim sorunları  
 Yönetilen barındırma ortamları kodda yalıtmak için çeşitli derlemeler için izin düzeylerini azaltma açık İlkesi ile birden çok alt uygulama etki alanları oluşturmak için yaygındır. Bununla birlikte, varsayılan uygulama etki alanında bu derlemeler için ilke değişmeden kalır. Bir alt uygulama etki alanlarının bir derlemeyi yüklemek için varsayılan uygulama etki alanı zorunlu kılabilirsiniz, kod yalıtım etkisini kaybolur ve zorla yüklü bütünleştirilmiş kodundaki türler daha yüksek bir güven düzeyinde kodu çalıştırmak mümkün olacaktır.  
  
 Uygulama etki alanı, bir derlemeyi yüklemek ve diğer uygulama etki alanında barındırılan bir nesne için bir proxy çağırarak içlerindeki kodu çalıştırmak için başka bir uygulama etki alanı zorlayabilirsiniz. Bir uygulama etki alanları arası proxy almak için nesneyi barındırma uygulama etki alanı yöntemi çağrısı parametre veya dönüş değerindeki aracılığıyla dağıtmanız gerekir. Veya, uygulama etki alanı yalnızca oluşturulmuş olsa bile, bir proxy Oluşturucusu olan <xref:System.AppDomain> varsayılan nesne. Bu nedenle, yalıtım kodu bozmayı önlemek için daha yüksek bir güven düzeyi içeren bir uygulama etki alanı sıralanmış-tarafından-başvuru nesnelere başvurular dağıtmak değil (sınıfından türetilen sınıfların örneklerini <xref:System.MarshalByRefObject>) düşük ile uygulama etki alanlarına etki alanında güven düzeyleri.  
  
 Genellikle, varsayılan uygulama etki alanı ile denetim nesnesi içindeki her bir uygulama etki alanları alt oluşturur. Denetim nesnesi yeni uygulama etki alanı yönetir ve bazen varsayılan uygulama etki alanından siparişleri alır, ancak bu gerçekten etki alanını doğrudan iletişim kuramaz. Bazen, varsayılan uygulama etki alanı kendi proxy denetimi nesneye çağırır. Bununla birlikte, varsayılan uygulama etki alanına geri çağırmaya denetim nesnesi için gerekli olduğu durumlar olabilir. Bu durumlarda, varsayılan uygulama etki alanı denetim nesnesi oluşturucusuna bir başvuruya göre geri çağırma nesnesi geçirir. Bu proxy korumak için denetimi nesnesinin sorumluluğundadır. Denetim nesnesi üzerinde bir genel sınıfın genel statik alan proxy yerleştirmeniz ya da proxy aksi genel olarak kullanıma sunmak için varsa, bu tehlikeli bir varsayılan uygulama etki alanına geri aramayı başka bir kod mekanizma açılacaktır. Bu nedenle, Denetim nesneler her zaman proxy özel olarak saklamak için örtük olarak güvenilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
