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
ms.openlocfilehash: bdc9d6e954c75ccfeea15ec163bc81e7a3ab8ab7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300703"
---
# <a name="create-and-use-strong-named-assemblies"></a>Tanımlayıcı adlı derlemeler oluşturma ve kullanma

Güçlü bir ad derlemenin kimliğinden oluşur — basit metin adı, sürüm numarasını ve (sağlanmışsa) kültür bilgilerini — artı ortak bir anahtardan ve dijital imza. Karşılık gelen özel anahtarı kullanarak bir derleme dosyasından oluşturuldu. (Derleme dosya adları ve derlemeyi oluşturan tüm dosyaların karma değerlerini içeren derleme bildirimini içerir.)

> [!WARNING]
> Güvenlik için tanımlayıcı adlar güvenmeyin. Benzersiz bir kimliğe sağlarlar.

Tanımlayıcı adlı bütünleştirilmiş kod, yalnızca diğer güçlü adlı derlemelere türlerinden kullanabilirsiniz. Aksi takdirde, tanımlayıcı adlı bütünleştirilmiş kodun bütünlüğünün tehlikede olması.

## <a name="strong-name-scenario"></a>Tanımlayıcı ad senaryosu

Bir derlemeyi katı bir adla imzalama ve daha sonra bu adla başvurduğu işlemini aşağıdaki senaryosu açıklanmaktadır.

1. Aşağıdaki yöntemlerden birini kullanarak güçlü bir adla derlemesi oluşturulur:

    -   Visual Studio gibi güçlü adlar oluşturma destekleyen bir geliştirme ortamı kullanarak.

    -   Kullanarak şifreleme anahtar çifti oluşturma [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) ve bu anahtar çifti kullanarak derleme komut satırı derleyicisi atama veya [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Windows Yazılım Geliştirme Seti (SDK), Sn.exe hem Al.exe sağlar.

2. Geliştirme ortamı veya aracı geliştiricinin özel anahtara sahip derleme bildirimini içeren dosyayı karma imzalar. Bu dijital imza A derleme bildirimini içeren taşınabilir yürütülebilir (PE) dosyasında depolanır.

3. Derleme B derleme A'ya tüketicisidir Derleme B'nin bildiriminin başvuru bölümüne derleme A'ın ortak anahtarını temsil eden bir belirteci içerir. Bir belirteç, tam ortak anahtarı bir bölümüdür ve anahtarı yerine alanından tasarruf etmek için kullanılır.

4. Ortak dil çalışma zamanı tanımlayıcı ad imzası, derlemeyi genel derleme önbelleğinde yerleştirildiğinde doğrular. Tanımlayıcı ad tarafından çalışma zamanında bağlanırken, ortak dil çalışma zamanı, A. derlemenin tanımlayıcı adı oluşturmak için kullanılan anahtarı ile derleme B'nin bildiriminde depolanan anahtar karşılaştırır. .NET Framework güvenlik denetimlerinin tamamlandığından ve bağlama işlemi başarılı olursa derleme B derleme A BITS ile oynanmadığını olduğunu ve bu BITS gerçekten derleme A'ya geliştiricilerden gelen garantisi sahip

> [!NOTE]
> Bu senaryo, güven sorunları ele almaz. Tam Microsoft Authenticode imzaları, ek bir tanımlayıcı ad derlemeleri gerçekleştirebilirsiniz. Authenticode imza güven oluşturur bir sertifika içerir. Güçlü adlar bu şekilde imzalanması için kod gerektirmeyen dikkat edin önemlidir. Güçlü adlar, yalnızca bir benzersiz kimliği sağlayın.

## <a name="bypass-signature-verification-of-trusted-assemblies"></a>İmza doğrulaması güvenilen derlemeleri atlama

İle başlayarak [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], tanımlayıcı ad imzaları, bir derleme için varsayılan uygulama etki alanı gibi bir tam güvenilir uygulamanızı etki alanına yüklendiğinde doğrulanmaz `MyComputer` bölge. Bu atlama özelliğini tanımlayıcı ad adlandırılır. İçin tam güven ortamında, talepleri <xref:System.Security.Permissions.StrongNameIdentityPermission> imzalarına bağımsız olarak tam güven derlemeleri imzalı için her zaman başarılı. Tanımlayıcı adlı atlama özelliği, daha hızlı derlemeler sağlar, bu durumda, tam güven derleme tanımlayıcı ad imzası doğrulama gereksiz yükünü ortadan kaldırır.

Atlama özelliği, güçlü bir adla imzalanır ve aşağıdaki özelliklere sahip herhangi bir derleme için geçerlidir:

-   Olmadan tam olarak güvenilen <xref:System.Security.Policy.StrongName> kanıt (örneğin, `MyComputer` kanıt bölge).

-   Tam olarak güvenilen yüklenen <xref:System.AppDomain>.

-   Bir konumdan yüklenen <xref:System.AppDomainSetup.ApplicationBase%2A> , söz konusu özellik <xref:System.AppDomain>.

-   Gecikmeli imzalanmış değil.

Bu özellik tek tek uygulamalar için veya bir bilgisayar için devre dışı bırakılabilir. Bkz: [nasıl yapılır: Tanımlayıcı adlı atlama özelliğini devre dışı](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: Genel-Özel Anahtar Çifti Oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)|Bir derlemeyi imzalamak için bir şifreleme anahtarı çiftiniz oluşturmayı açıklar.|
|[Nasıl yapılır: Derlemeyi Tanımlayıcı Adla İmzalama](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)|Tanımlayıcı adlı bir derlemenin nasıl oluşturulacağını açıklar.|
|[Güçlü Adlandırmayı İyileştirme](../../../docs/framework/app-domains/enhanced-strong-naming.md)|Güçlü-adlarında yapılan geliştirmeleri açıklar [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|
|[Nasıl yapılır: Tanımlayıcı Adlı Bir Derlemeye Başvurma](../../../docs/framework/app-domains/how-to-reference-a-strong-named-assembly.md)|Türler veya kaynaklar tanımlayıcı adlı bütünleştirilmiş kod derleme zamanında başvuru veya çalışma zamanı açıklar.|
|[Nasıl yapılır: Tanımlayıcı Adlı Atlama Özelliğini Devre Dışı Bırakma](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)|Tanımlayıcı ad imzası doğrulama atlar özelliği devre dışı açıklar. Bu özellik tüm veya belirli uygulamalar için devre dışı bırakılabilir.|
|[Derlemeler Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)|Tek dosya ve çok dosyalı derlemeler genel bir bakış sağlar.|
|[Visual Studio'da derlemeyi imzala nasıl](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Derleme oluşturulduktan sonra bir derlemeyi katı bir adla imzalamak kullanılan nasıl açıklanmaktadır.|
|[Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)|Derlemeleri tanımlayıcı adlarla oluşturulmasına yardımcı olan .NET Framework içindeki aracı açıklar. Bu araç, temel yönetim, imza oluşturma ve imza doğrulaması için seçenekler sağlar.|
|[Al.exe (Derleme Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)|Modüller ya da kaynak dosyalarından derleme bildirimi içeren bir dosya oluşturur, .NET Framework içindeki aracı açıklar.|
