---
title: Tanımlayıcı Adlı Derlemeler Oluşturma ve Kullanma
ms.date: 08/01/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, about strong-named assemblies
- strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, scenarios
- assemblies [.NET Framework], strong-named
- strong-named assemblies, loading into trusted application domains
- assembly binding, strong-named
ms.assetid: ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94659919d4e902f8562e669fbb0f98d6ebc679ab
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744648"
---
# <a name="creating-and-using-strong-named-assemblies"></a>Tanımlayıcı Adlı Derlemeler Oluşturma ve Kullanma
<a name="top"></a> Tanımlayıcı ad derlemenin kimliğini oluşur — basit metin adı, sürüm numarasını ve (sağladıysanız) kültür bilgilerini — bir ortak anahtar ve dijital imza artı. Karşılık gelen özel anahtarı kullanarak bir derleme dosyası oluşturulur. (Derleme dosyası adları ve derlemeyi oluşturan tüm dosyaların karmaları içeren derleme bildirimi içerir.)  
  
 Tanımlayıcı adlı bir derleme yalnızca diğer tanımlayıcı adlı derlemeler türlerinden kullanabilirsiniz. Tanımlayıcı adlı derleme bütünlüğünü tehlikeye Aksi takdirde.  
  
 Bu genel bakışta aşağıdaki bölümleri içerir:  
  
-   [Güçlü ad senaryosu](#strong_name_scenario)  
  
-   [Güvenilir derlemeler imza doğrulaması atlama](#bypassing_signature_verification)  
  
-   [İlgili Konular](#related_topics)  
  
<a name="strong_name_scenario"></a>   
## <a name="strong-name-scenario"></a>Güçlü ad senaryosu  
 Aşağıdaki senaryoda bir derlemeyi tanımlayıcı adla imzalama ve daha sonra bu adı başvuran süreci özetlenmektedir.  
  
1.  Derlemesi aşağıdaki yöntemlerden birini kullanarak için güçlü bir ad oluşturulur:  
  
    -   Güçlü oluşturma destekleyen bir geliştirme ortamı kullanarak ad gibi [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].  
  
    -   Kullanarak şifreleme anahtar çifti oluşturma [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) ve bu anahtar çifti ya da kullanarak derlemeye komut satırı derleyicisi atama veya [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Windows Yazılım Geliştirme Seti (SDK) Sn.exe ve Al.exe sağlar.  
  
2.  Geliştirme ortamı veya aracı geliştiricinin özel anahtarla derleme bildirimi içeren dosyanın karması imzalar. Bu dijital imza derleme A'ın bildirimi içeren taşınabilir yürütülebilir (PE) dosyasında depolanır.  
  
3.  Derleme B derleme A. tüketicisidir Derleme B'nin bildirimi başvurusu bölümü derleme A'ın genel anahtarı temsil eden bir belirteci içerir. Belirteç tam ortak anahtarı bir kısmı ve anahtar yerine alanından tasarruf etmek için kullanılır.  
  
4.  Genel derleme önbelleğinde derleme yerleştirildiğinde ortak dil çalışma zamanı sağlam ad imzası doğrular. Güçlü adıyla çalışma zamanında bağlanırken, ortak dil çalışma zamanı derlemesi A. için güçlü adı oluşturmak için kullanılan anahtar ile derleme B'nin bildiriminde depolanan anahtar karşılaştırır. .NET Framework güvenliği denetimlerinin ve bağlama başarılı derleme B derleme A'ın BITS ile oynanmadığını olduğunu ve bu BITS derlemesinin A. geliştiricilerden gerçekte gelen bir garantisi yoktur  
  
> [!NOTE]
>  Bu senaryo, güven sorunları adresi değil. Derlemelerin tanımlayıcı ad yanı sıra tam Microsoft Authenticode imzaları taşıyabilir. Authenticode imzaları güven oluşturur bir sertifika içerir. Tanımlayıcı adlar bu şekilde imzalanmasını kodu gerektirmeyen dikkate almak önemlidir. Tanımlayıcı adlar yalnızca benzersiz bir kimlik belirtin.  
  
 [Başa dön](#top)  
  
<a name="bypassing_signature_verification"></a>   
## <a name="bypassing-signature-verification-of-trusted-assemblies"></a>Güvenilir derlemeler imza doğrulaması atlama  
 İle başlayarak [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], güçlü ad imzaları bütünleştirilmiş varsayılan uygulama etki alanı gibi bir tam güven uygulama etki alanına yüklendiğinde doğrulanmaz `MyComputer` bölgesi. Bu özellik güçlü-adı olarak atlamak için adlandırılır. İçin tam güven ortamında, talep <xref:System.Security.Permissions.StrongNameIdentityPermission> imzalı için tam güven derlemeler, bunların imza bağımsız olarak her zaman başarılı. Tanımlayıcı adlı atlama özelliği sağlam ad imzası doğrulama derlemelerin daha hızlı yük derlemeleri izin vererek tam güven bu durumda, gereksiz ek yükü ortadan kaldırır.  
  
 Atlama özelliğini tanımlayıcı bir ad ile imzalanmış ve aşağıdaki özelliklere sahip herhangi bir derlemeye geçerlidir:  
  
-   Tam olarak güvenilmeyen olmadan <xref:System.Security.Policy.StrongName> kanıt (örneğin, sahip `MyComputer` bölge kanıt).  
  
-   Bir tam olarak güvenilmeyen yüklenen <xref:System.AppDomain>.  
  
-   Altında bir konumdan yüklenen <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği, <xref:System.AppDomain>.  
  
-   Gecikme imzalı değil.  
  
 Bu özellik bağımsız uygulamalar için veya bir bilgisayar için devre dışı bırakılabilir. Bkz: [nasıl yapılır: tanımlayıcı adlı atlama özelliğini devre dışı](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
 [Başa dön](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Genel-Özel Anahtar Çifti Oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)|Bir derlemeyi imzalamak için şifreleme anahtar çiftinin oluşturmayı açıklar.|  
|[Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)|Tanımlayıcı adlı bir derleme oluşturmayı açıklar.|  
|[Gelişmiş Kesin Adlandırma](../../../docs/framework/app-domains/enhanced-strong-naming.md)|Güçlü-adlarında geliştirmeler açıklanmaktadır [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|[Nasıl yapılır: Kesin Adlandırılmış bir Bütünleştirilmiş Koda Başvurma](../../../docs/framework/app-domains/how-to-reference-a-strong-named-assembly.md)|Türleri veya tanımlayıcı adlı bir derlemeye çalışma zamanında kaynaklarında başvuru veya çalışma zamanı açıklar.|  
|[Nasıl yapılır: Kesin Adlandırılmış Atlama Özelliğini Devre Dışı Bırakma](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)|Tanımlayıcı adlı imza doğrulaması atlar özelliğini devre dışı bırakmak açıklar. Bu özellik tüm için veya belirli uygulamalar için devre dışı bırakılabilir.|  
|[Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)|Tek dosya ve birden çok dosya derlemeleri genel bir bakış sağlar.|  
|[Visual Studio'da bir derlemeyi oturum gecikme nasıl](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Derleme oluşturulduktan sonra bir derlemeyi tanımlayıcı adla oturum açıklanmaktadır.|  
|[Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)|Tanımlayıcı adlar ile derlemeleri oluşturmaya yardımcı olan .NET Framework dahil anlatır. Bu araç, temel yönetim, imza oluşturma ve imza doğrulaması için seçenekler sağlar.|  
|[Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)|Modülleri ya da kaynak dosyaları bildirim bütünleştirilmiş sahip bir dosya oluşturur .NET Framework'teki içerdiği aracı açıklar.|
