---
title: Derleme sürümü oluşturma
ms.date: 08/20/2019
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
ms.openlocfilehash: bbb3dae2ce66c93d05a2a1c0f7e426901fa7b2e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140183"
---
# <a name="assembly-versioning"></a>Derleme sürümü oluşturma

Ortak dil çalışma zamanını kullanan tüm derlemelerin sürüm oluşturma işlemi, derleme düzeyinde gerçekleşir. Bir derlemenin belirli sürümü ve bağımlı derlemelerin sürümleri, derlemenin bildirimine kaydedilir. Çalışma zamanı için varsayılan sürüm ilkesi, yapılandırma dosyalarındaki sürüm ilkelerinde açıkça geçersiz kılınmadığı sürece (uygulama yapılandırma dosyası, yayımcı ilke dosyası ve bilgisayar yöneticisinin yapılandırma dosyası) uygulamaların yalnızca yapılandırıldığı ve test edildiği sürümlerle çalışmasıdır.  
  
> [!NOTE]
> Sürüm oluşturma yalnızca tanımlayıcı ada sahip derlemeler üzerinde yapılır.  
  
Çalışma zamanı, bir derleme bağlama isteğini çözmek için birkaç adım gerçekleştirir:  
  
1. Bağlanacak derlemenin sürümünü belirlemek için orijinal derleme başvurusunu denetler.  
  
2. Sürüm ilkesini uygulamak için uygulanabilir tüm yapılandırma dosyalarını denetler.  
  
3. Orijinal derleme başvurusundan ve yapılandırma dosyalarında belirtilen yeniden yönlendirmelerden doğru derlemeyi belirler ve çağıran derlemeye bağlanacak olan sürümü belirler.  
  
4. Genel derleme önbelleğini, yapılandırma dosyalarında belirtilen kod tabanlarını denetler ve [çalışma zamanının derlemeleri nasıl yer lediğini](../../framework/deployment/how-the-runtime-locates-assemblies.md)açıklayan sondalama kurallarını kullanarak uygulamanın dizinini ve alt dizinlerini denetler.  
  
Aşağıdaki resimde şu adımlar gösterilmektedir:  
  
![Derleme bağlama isteği çözümündeki adımları gösteren diyagram.](./media/versioning/resolve-assembly-binding-request.gif)
  
Uygulamaları yapılandırma hakkında daha fazla bilgi için uygulamaları [Yapılandır'a](../../framework/configure-apps/index.md)bakın. Bağlama ilkesi hakkında daha fazla bilgi için [çalışma zamanının derlemeleri nasıl bulabildiğini](../../framework/deployment/how-the-runtime-locates-assemblies.md)görün.  
  
## <a name="version-information"></a>Sürüm bilgileri  

Her derlemenin sürüm bilgisini ifade etmek için iki farklı yolu vardır:  
  
- Derleme adı ve kültür bilgisiyle birlikte derlemenin kimliğinin bir parçası olan derleme sürüm numarası. Bu numara çalışma zamanı tarafından sürüm ilkesini uygulamak için kullanılır ve çalışma zamanında tür çözümleme işleminde önemli bir rol oynar.  
  
- Sadece bilgi amaçlı olarak eklenen ek sürüm bilgilerini temsil eden bir dize olan bilgilendirme sürümü.  
  
### <a name="assembly-version-number"></a>Montaj sürüm numarası  

Her derleme, kimliğinin bir parçası olarak bir sürüm numarasına sahiptir. Bu nedenle, sürüm numarası farklı olan iki derleme, çalışma zamanı tarafından tamamen farklı derlemeler olarak değerlendirilir. Bu sürüm numarası, fiziksel olarak aşağıdaki biçime sahip dört bölümlü bir dize olarak temsil edilir:  
  
\<*ana sürümü*>. \< *küçük sürümü*>. \< *> sayısı oluşturun.* \< *revizyon*>  
  
Örneğin, 1.5.1254.0 sürümü ana sürüm olarak 1, alt sürüm olarak 5, yapı numarası olarak 1254 ve düzeltme numarası olarak da 0 belirtir.  
  
Sürüm numarası, derleme adı ve ortak anahtarı içeren kimlik bilgisinin yanı sıra ilişkiler hakkında bilgi ve uygulamayla bağlı olan diğer derlemelerin kimlikleriyle birlikte derleme bildiriminde saklanır.  
  
Bir derleme yapılandırıldığında, geliştirme aracı derleme bildiriminde atıf yapılan her derleme için bağımlılık bilgisi kaydeder. Çalışma zamanı bu sürüm numaralarını bir yönetici, uygulama veya yayımcı tarafından ayarlanan yapılandırma bilgisiyle birlikte kullanarak başvurulan bir derlemenin uygun sürümünü yükler.  
  
Çalışma zamanı, normal ve tanımlayıcı ada sahip derlemeleri sürüm oluşturma amacıyla ayırt eder. Sürüm denetleme yalnızca tanımlayıcı ada sahip derlemelerde gerçekleşir.  
  
Sürüm bağlama ilkeleri belirtme hakkında bilgi için [bkz.](../../framework/configure-apps/index.md) Çalışma zamanının belirli bir derlemeyi bulmak için sürüm bilgilerini nasıl kullandığı hakkında bilgi [için, çalışma zamanının derlemeleri nasıl bulduğuna](../../framework/deployment/how-the-runtime-locates-assemblies.md)bakın.  
  
### <a name="assembly-informational-version"></a>Derleme bilgilendirme sürümü  

Bilgilendirme sürümü, bir derlemeye yalnızca bilgilendirme amacıyla ek sürüm bilgileri ekleyen bir dizedir; bu bilgi çalışma zamanında kullanılmaz. Metin tabanlı bilgilendirme sürümü, ürünün pazarlama belgelerine, paketlemesine veya ürün adına karşılık gelir ve çalışma zamanı tarafından kullanılmaz. Örneğin, bir bilgilendirme sürümü "Ortak Dil Çalışma Zamanı sürüm 1.0" veya "NET Control SP 2" olabilir. Microsoft Windows'daki dosya özellikleri iletişim kutusunun Sürüm sekmesinde, bu bilgi "Ürün Sürümü" öğesinde görünür.  
  
> [!NOTE]
> Herhangi bir metni ayarlayabilseniz de dize derleme sürüm numarası tarafından kullanılan biçimde değilse veya o biçimdeyse ancak jokerler içeriyorsa derleme esnasında bir uyarı iletisi görünür. Bu uyarı zararsızdır.  
  
Bilgilendirme sürümü <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType> özel özniteliği kullanılarak temsil edilir. Bilgilendirişyelsürümü özniteliği hakkinda daha fazla bilgi için montaj [özniteliklerini ayarlay](set-attributes.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı derlemeleri nasıl bulur?](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Uygulama yapılandırma](../../framework/configure-apps/index.md)
- [Derleme özniteliklerini ayarlama](set-attributes.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
