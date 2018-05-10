---
title: Yönetilmeyen Kod İçin Güvenli Kodlama Yönergeleri
ms.date: 03/30/2017
helpviewer_keywords:
- code security, unmanaged code
- unmanaged code, securing
- security [.NET Framework], unmanaged code
- secure coding, unmanaged code
ms.assetid: a8d15139-d368-4c9c-a747-ba757781117c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60e293ac8c9100876aa5a524bb5dda04e9f4183f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="secure-coding-guidelines-for-unmanaged-code"></a>Yönetilmeyen Kod İçin Güvenli Kodlama Yönergeleri
Yönetilmeyen kod (örneğin, yerel kod gibi Win32 API'ları) çağırmak bazı kitaplık kodu gerekir. Bu yönetilen kod için güvenlik çevre dışında son giderek gösterdiğinden dikkat gereklidir. Tarafsız güvenlik kodunuzu ise hem kodunuz hem de çağırır herhangi bir kod kod izni yönetilmeyen gerekir (<xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> bayrağı belirtilmiş).  
  
 Ancak, genellikle, çağıran gibi güçlü izinlerine sahip olmasını aşırı olur. Böyle durumlarda, güvenilir kodunuzu yönetilen sarmalayıcı benzer aracılık olabilir veya kitaplık kodu açıklanan [sarmalayıcı kodunun güvenliğini sağlama](../../../docs/framework/misc/securing-wrapper-code.md). Temel yönetilmeyen kod işlevsellik tümüyle güvenli ise, doğrudan verilebilen; Aksi takdirde, uygun izni denetimi (isteğe bağlı) ilk gereklidir.  
  
 Yönetilmeyen koda kodunuzu çağırması ancak, çağrı yönetimsiz kod erişim iznine sahip gerektiren istemediğiniz durumlarda hak assert gerekir. Bir onaylama Çerçevenizi adresindeki yığın ilerlemesi engeller. Bu işlemde güvenlik delik oluşturmayın dikkatli olmanız gerekir. Genellikle, bu, arayanlar, uygun bir izin talep ve yalnızca ne bu izin verir ve artık gerçekleştirmek için yönetilmeyen kod kullanmak anlamına gelir. Bazı durumlarda (örneğin, bir get gün saat işlevi) yönetilmeyen kod doğrudan tüm güvenlik denetimleri olmadan arayanlara gösterilebilir. Herhangi bir durumda, onaylar herhangi bir kod güvenlik sorumluluğunu almanız gerekir.  
  
 Yerel kod içine bir kod yolu sağlayan herhangi bir yönetilen kod kötü amaçlı kod olası hedefi olduğundan, hangi yönetilmeyen kod belirleme güvenli bir şekilde kullanılabilmesi için ve son derece dikkatli olunmalıdır nasıl kullanılmalıdır gerektirir. Genellikle, yönetilmeyen kod hiçbir zaman doğrudan kısmen güvenilen arayanlara açılmamalıdır. Yönetilmeyen kod kullanımı kısmen güvenilen kod tarafından çağrılabilir kitaplıkları güvenliği hesaplama iki birincil noktalar vardır:  
  
-   **İşlevselliği**. Yönetilmeyen API potansiyel olarak tehlikeli olabilecek işlemlerini gerçekleştirmek arayanlara izin vermiyor işlevsellik sağlar mı? Kod erişimi güvenliği izinleri kaynaklarına erişimi zorlamak için bu nedenle API dosyaları, bir kullanıcı arabirimi kullanıp kullanmadığını göz önünde bulundurun kullanır veya iş parçacığı oluşturma, ya da bilgi korumalı olup olmadığını gösterir. Bulursa, onu kaydırma yönetilen kod girilmesi kendisine izin vermeden önce gerekli izinleri talep gerekir. Ayrıca, bir izin tarafından korunmayan olsa da, bellek erişimi için kesin tür güvenliği sınırlı gerekir.  
  
-   **Parametre denetimi**. Ortak bir saldırı geçişleri beklenmeyen parametreleri yönetilmeyen kod API yöntemlerini dışında belirtimi çalışmasına neden girişimi de sağlanmaktadır. Aralık çıkış dizini kullanarak arabellek taşmasına neden veya arka plandaki kod hatada yararlanabilir herhangi bir parametre olarak uzaklık değerleri bu tür saldırılar, yaygın bir örneği değil. Yönetilmeyen kod API (sonra gerekli taleplerini) kısmen güvenilir işlevsel olarak güvenli olsa bile bu nedenle, yönetilen arayanlar, gereken ayrıca ayrıntısına hiçbir istenmeyen çağrıları kötü amaçlı koddan yönetilen kullanarak olası olduğundan emin olmak için onay parametre geçerlilik kod kod sarmalayıcı katmanı.  
  
## <a name="using-suppressunmanagedcodesecurityattribute"></a>SuppressUnmanagedCodeSecurityAttribute Kullanma  
 Bir performans boy sunduğundan ve yönetilmeyen kodu çağırma yoktur. Her tür çağrısı için güvenlik sistemi otomatik olarak her zaman bir yığın ilerlemesi kaynaklanan yönetilmeyen kod iznine ihtiyaç duyar. Assert ve hemen yönetilmeyen kodu çağırma yığın ilerlemesi anlamsız olabilir:, assert ve yönetilmeyen kod aramanız oluşur.  
  
 Özel bir öznitelik adı verilen <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> talep normal güvenlik denetimi devre dışı bırakmak için yönetilmeyen kod giriş noktaları için uygulanabilir <xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> belirtilen izni. Bu eylem, çalışma zamanı güvenlik ile yönetilmeyen koda açık bir kapı oluşturduğundan, bunu denetlediğinde son derece dikkatli olun her zaman alınması gerekir. Not ettiğiniz, hatta ile **SuppressUnmanagedCodeSecurityAttribute** uygulanan, anında arayanlar çağırma izni olduğundan emin olmak için tam zamanında (JIT) derleme olur bir kerelik güvenlik denetimi yoktur yönetilmeyen kod.  
  
 Kullanırsanız **SuppressUnmanagedCodeSecurityAttribute**, aşağıdaki noktaları denetleyin:  
  
-   Yönetilmeyen kod giriş noktası iç ya da kodunuzu dışında herhangi bir şekilde erişilemez olun.  
  
-   Tüm yönetilmeyen koda olası bir güvenlik delik çağrıdır. Kodunuzu dolaylı olarak yönetilmeyen koda çağırın ve güvenlik denetimi önlemek kötü amaçlı kod için bir portal olmadığından emin olun. İzinler, uygunsa talep.  
  
-   Aşağıdaki bölümde açıklandığı gibi yönetilmeyen koda tehlikeli yolu oluştururken açıkça tanımlamak için bir adlandırma kuralını kullanın...  
  
## <a name="naming-convention-for-unmanaged-code-methods"></a>Yönetilmeyen kod yöntemleri için adlandırma kuralı  
 Yönetilmeyen kod yöntemleri adlandırmak için kullanışlı ve yüksek oranda önerilen kuralı kuruldu. Tüm yönetilmeyen kod yöntemleri üç kategoriye ayrılır: **güvenli**, **yerel**, ve **güvensiz**. Bu anahtar sözcükler içinde çeşitli yönetilmeyen kod giriş noktaları tanımlanan sınıf adları kullanılabilir. Kaynak kodunda bu anahtar sözcükler sınıf adı olarak eklenmesi gerektiğini `Safe.GetTimeOfDay`, `Native.Xyz`, veya `Unsafe.DangerousAPI`, örneğin. Aşağıdaki tabloda açıklandığı gibi her şu anahtar sözcüklerden biri o sınıfın kullanan geliştiriciler için yararlı bir güvenlik bilgileri sağlar.  
  
|Anahtar sözcüğü|Güvenlik konuları|  
|-------------|-----------------------------|  
|**Güvenli**|Herhangi bir kod için çağırmak için bile kötü amaçlı kod zararsız tamamen. Diğer yönetilen kod gibi kullanılabilir. Örneğin, günün saatini alır bir işlev genellikle güvenlidir.|  
|**Yerel**|Tarafsız güvenlik; diğer bir deyişle, kodu çağırma izni gerektiren yönetilmeyen kod yönetilmeyen. Güvenlik, yetkisiz bir arayan vermemeye denetlenir.|  
|**unsafe**|Gizlenen güvenlik potansiyel olarak tehlikeli olabilecek yönetilmeyen kod giriş noktası. Geliştiriciler en dikkat gibi yönetilmeyen kod kullanırken diğer korumaları bir güvenlik açığı önlemek için yerine getirildiğinden emin kullanmalıdır. Bu anahtar sözcük güvenlik sistemi geçersiz kılmaları geliştiriciler sorumlu olması gerekir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
