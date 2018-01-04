---
title: "Güvenli Kodlama Yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET Framework], security
- code security, options
- security-neutral code
- security [.NET Framework], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3e75f3c74c5966ce5ce22b23f7ba179e903d37aa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="secure-coding-guidelines"></a>Güvenli Kodlama Yönergeleri
Kanıt tabanlı güvenlik ve kod erişim güvenliği güvenlik uygulamak çok güçlü, açık mekanizmaları sağlar. Çoğu uygulama kodu yalnızca .NET Framework tarafından uygulanan altyapısını kullanabilir. Bazı durumlarda, ek uygulamaya özgü güvenlik güvenlik sistemini genişletme veya yeni geçici yöntemleri kullanarak yerleşik gereklidir.  
  
 .NET Framework tarafından zorlanan izinleri ve diğer uygulama kodunuzda kullanarak, kötü amaçlı kod olmasını istemediğinizi bilgilerini elde etmeyi veya istenmeyen diğer eylemler gerçekleştiriyorsa önlemek için engelleri erect. Ayrıca, güvenlik ve kullanılabilirlik arasında bir denge güvenilen kod kullanarak tüm beklenen senaryolarda üstünü gerekir.  
  
 Bu genel bakışta kodu güvenlik sistemi ile çalışmak için tasarlanmış farklı yolları açıklanmaktadır.  
  
## <a name="securing-resource-access"></a>Kaynak erişimini güvenli hale getirme  
 Tasarlama ve kodunuzu yazmaya korumak ve özellikle kullanırken veya bilinmeyen kod yürütmesini kaynaklarına koduna sahip erişimi sınırlamak gerekir. Bu nedenle, kodunuzu güvenli olduğundan emin olmak için aşağıdaki teknikleri göz önünde bulundurun:  
  
-   Kod erişim güvenliği (CAS) kullanmayın.  
  
-   Kısmen güvenilen kod kullanmayın.  
  
-   .NET uzaktan iletişim kullanmayın.  
  
-   Dağıtılmış Bileşen Nesne Modeli (DCOM) kullanmayın.  
  
-   İkili biçimlendiricileri kullanmayın.  
  
 Kod erişimi güvenliği ve güvenliği saydam kod kısmen güvenilen kod güvenlik sınırı olarak desteklenmeyeceğini. Bilinmeyen kaynaklardan gelen kodların, alternatif güvenlik önlemleri alınmadan yüklenmesi ve yürütülmesi önerilmez. Alternatif güvenlik önlemleri şunlardır:  
  
-   Sanallaştırma  
  
-   AppContainers  
  
-   İşletim sistemi (OS) kullanıcılar ve izinler  
  
-   Hyper-V kapsayıcıları  
  
## <a name="security-neutral-code"></a>Tarafsız güvenlik kodu  
 Tarafsız güvenlik kodu bir güvenlik sistemi açık hiçbir şey yapmaz. Hangi izinlerle onu çalıştırır alır. Korumalı işlemleri (örneğin, dosya, ağ vb. kullanarak) ile ilişkili güvenlik özel durumları yakalamak için başarısız uygulamaları içinde işlenmeyen bir özel yol açabilecek olsa da Tarafsız güvenlik kodu hala .NET Framework güvenliği yararlanır teknolojileri.  
  
 Tarafsız güvenlik kitaplığı anlamanız gereken özel özelliklere sahiptir. Kitaplık dosyaları kullanan veya yönetilmeyen kodu çağırma API öğeleri sağlar varsayın. kodunuzu karşılık gelen izni yoksa açıklandığı gibi çalışmaz. Bununla birlikte, kod izni olsa bile, çağıran herhangi bir uygulama kodu çalışması için aynı izni olmalıdır. Çağrıyı yapan kod sağ izni yoksa bir <xref:System.Security.SecurityException> sonucunda kod erişim güvenliği yığın ilerlemesi görüntülenir.  
  
## <a name="application-code-that-is-not-a-reusable-component"></a>Yeniden kullanılabilir bileşen olmayan uygulama kodu  
 Kodunuzu diğer kodu tarafından çağrılmaz bir uygulamanın parçası ise, güvenlik basittir ve özel kodlama gerekli olmayabilir. Bununla birlikte, kötü amaçlı kod kodunuzu çağırabilirsiniz unutmayın. Kod erişim güvenliği kaynaklara erişmesini kötü amaçlı kod durdurabilir olsa da, bu tür kodu hala alanları veya hassas bilgiler içerebilir özellikleri değerler okuyabilir.  
  
 Ayrıca, kullanıcı girişi Internet'ten veya diğer güvenilir olmayan kaynaklardan kodunuzu kabul ederse, kötü amaçlı girişi hakkında dikkatli olmalıdır.  
  
## <a name="managed-wrapper-to-native-code-implementation"></a>Sarmalayıcı yerel kod uygulamasına yönetilen  
 Genellikle bu senaryoda, yararlı işlevselliğinin yönetilen kod için kullanılabilir hale getirmek istediğiniz yerel kodda uygulanır. Yönetilen sarmalayıcılar, yazma ya da platform çağırma kullanma veya COM birlikte çalışma için kolaydır. Ancak, bunu yaparsanız, sarmalayıcıları arayanlar başarılı olması için yönetilmeyen kod haklarına sahip olmalıdır. Varsayılan ilke altında bu kod intranetten indirilebilir veya Internet ile sarmalayıcıları çalışmaz anlamına gelir.  
  
 Bu sarmalayıcıları yönetilmeyen kod hakları kullanan tüm uygulamalar vermek yerine, yalnızca sarmalayıcı kodu bu hakları vermek iyidir. Kaynak temel işlevselliği sunar ve uygulama benzer şekilde güvenli ise, sarmalayıcı yalnızca kendi hakları assert üzerinden çağırmak herhangi bir kod sağlayan gerekir. Kaynaklar dahil edildiğinde güvenlik kodlama sonraki bölümde açıklanan kitaplık kodu çalışması ile aynı olmalıdır. Sarmalayıcı potansiyel olarak bu kaynakları arayanlara gösterme olduğundan, bir yerel kod dikkatli doğrulanması gereklidir ve sarmalayıcının sorumluluğundadır.  
  
## <a name="library-code-that-exposes-protected-resources"></a>Korunan kaynakları gösteren kitaplık kodu  
 Bu en güçlü ve bu nedenle (yanlışlıkla yapıldıysa) potansiyel olarak tehlikeli olabilecek güvenlik kodlama için yaklaşımı: kitaplığınızın Aksi durumda, yalnızca .NET Framework sınıfları kullanılabilir değil belirli kaynaklara erişmek başka bir kod için bir arabirim olarak hizmet kullandıkları kaynaklara izinlerini uygulayın. Bir kaynak kullanıma olduğunda, kodunuzu kaynağa uygun izni ilk talep gerekir (diğer bir deyişle, bu bir güvenlik denetimi gerçekleştirmeniz gerekir) ve genellikle gerçek işlemi gerçekleştirmek için kendi haklarını assert.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Durum Verilerinin Güvenliğini Sağlama](../../../docs/standard/security/securing-state-data.md)|Özel üyelerin korumak açıklar.|  
|[Güvenlik ve Kullanıcı Girdisi](../../../docs/standard/security/security-and-user-input.md)|Bu kullanıcı girişi kabul eden uygulamalar ile ilgili güvenlik konuları açıklanmaktadır.|  
|[Güvenlik ve Yarış Durumları](../../../docs/standard/security/security-and-race-conditions.md)|Yarış durumları kodunuzda önlemek açıklar.|  
|[Güvenlik ve Çalışma Sırasında Kod Oluşturma](../../../docs/standard/security/security-and-on-the-fly-code-generation.md)|Dinamik kodu oluşturmak uygulamalar ile ilgili güvenlik konuları açıklanmaktadır.|  
|[Rol Tabanlı Güvenlik](../../../docs/standard/security/role-based-security.md)|.NET Framework rol tabanlı güvenlik ayrıntılı açıklar ve kodunuzda kullanma yönergeleri sağlar.|
