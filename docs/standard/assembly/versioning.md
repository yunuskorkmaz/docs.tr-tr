---
title: Derleme sürümü oluşturma
description: .NET derlemelerinin sürümü oluşturma hakkında bilgi edinin. CLR kullanan derlemelerin tüm sürümü derleme düzeyinde yapılır.
ms.date: 08/20/2019
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
ms.openlocfilehash: fdffbcc0bbafed62228cba35e8f85fbec7f7fbab
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380078"
---
# <a name="assembly-versioning"></a>Derleme sürümü oluşturma

Ortak dil çalışma zamanını kullanan tüm derlemelerin sürüm oluşturma işlemi, derleme düzeyinde gerçekleşir. Bir derlemenin belirli sürümü ve bağımlı derlemelerin sürümleri, derlemenin bildirimine kaydedilir. Çalışma zamanı için varsayılan sürüm ilkesi, yapılandırma dosyalarındaki sürüm ilkelerinde açıkça geçersiz kılınmadığı sürece (uygulama yapılandırma dosyası, yayımcı ilke dosyası ve bilgisayar yöneticisinin yapılandırma dosyası) uygulamaların yalnızca yapılandırıldığı ve test edildiği sürümlerle çalışmasıdır.  
  
> [!NOTE]
> Sürüm oluşturma yalnızca tanımlayıcı ada sahip derlemeler üzerinde yapılır.  
  
Çalışma zamanı, bir derleme bağlama isteğini çözmek için birkaç adım gerçekleştirir:  
  
1. Bağlanacak derlemenin sürümünü belirlemek için orijinal derleme başvurusunu denetler.  
  
2. Sürüm ilkesini uygulamak için uygulanabilir tüm yapılandırma dosyalarını denetler.  
  
3. Orijinal derleme başvurusundan ve yapılandırma dosyalarında belirtilen yeniden yönlendirmelerden doğru derlemeyi belirler ve çağıran derlemeye bağlanacak olan sürümü belirler.  
  
4. Yapılandırma dosyalarında belirtilen genel derleme önbelleğini ve kod temellerini denetler ve [çalışma zamanının derlemeleri nasıl](../../framework/deployment/how-the-runtime-locates-assemblies.md)konumlandırdığını açıklanan yoklama kurallarını kullanarak uygulamanın dizinini ve alt dizinlerini denetler.  
  
Aşağıdaki çizimde bu adımlar gösterilmektedir:  
  
![Derleme bağlama isteği çözümlemesindeki adımları gösteren diyagram.](./media/versioning/resolve-assembly-binding-request.gif)
  
Uygulamaları yapılandırma hakkında daha fazla bilgi için bkz. [uygulamaları yapılandırma](../../framework/configure-apps/index.md). Bağlama ilkesi hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md).  
  
## <a name="version-information"></a>Sürüm bilgileri  

Her derlemenin sürüm bilgisini ifade etmek için iki farklı yolu vardır:  
  
- Derleme adı ve kültür bilgisiyle birlikte derlemenin kimliğinin bir parçası olan derleme sürüm numarası. Bu numara çalışma zamanı tarafından sürüm ilkesini uygulamak için kullanılır ve çalışma zamanında tür çözümleme işleminde önemli bir rol oynar.  
  
- Sadece bilgi amaçlı olarak eklenen ek sürüm bilgilerini temsil eden bir dize olan bilgilendirme sürümü.  
  
### <a name="assembly-version-number"></a>Derleme sürüm numarası  

Her derleme, kimliğinin bir parçası olarak bir sürüm numarasına sahiptir. Bu nedenle, sürüm numarası farklı olan iki derleme, çalışma zamanı tarafından tamamen farklı derlemeler olarak değerlendirilir. Bu sürüm numarası, fiziksel olarak aşağıdaki biçime sahip dört bölümlü bir dize olarak temsil edilir:  
  
\<*ana sürüm*>. \< *ikincil sürüm*>. \< *Yapı numarası*>. \< *Düzeltme*>  
  
Örneğin, 1.5.1254.0 sürümü ana sürüm olarak 1, alt sürüm olarak 5, yapı numarası olarak 1254 ve düzeltme numarası olarak da 0 belirtir.  
  
Sürüm numarası, derleme adı ve ortak anahtarı içeren kimlik bilgisinin yanı sıra ilişkiler hakkında bilgi ve uygulamayla bağlı olan diğer derlemelerin kimlikleriyle birlikte derleme bildiriminde saklanır.  
  
Bir derleme yapılandırıldığında, geliştirme aracı derleme bildiriminde atıf yapılan her derleme için bağımlılık bilgisi kaydeder. Çalışma zamanı bu sürüm numaralarını bir yönetici, uygulama veya yayımcı tarafından ayarlanan yapılandırma bilgisiyle birlikte kullanarak başvurulan bir derlemenin uygun sürümünü yükler.  
  
Çalışma zamanı, normal ve tanımlayıcı ada sahip derlemeleri sürüm oluşturma amacıyla ayırt eder. Sürüm denetleme yalnızca tanımlayıcı ada sahip derlemelerde gerçekleşir.  
  
Sürüm bağlama ilkelerini belirtme hakkında bilgi için bkz. [uygulamaları yapılandırma](../../framework/configure-apps/index.md). Çalışma zamanının belirli bir derlemeyi bulmak için sürüm bilgilerini nasıl kullandığı hakkında bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md).  
  
### <a name="assembly-informational-version"></a>Derleme bilgilendirici sürümü  

Bilgilendirme sürümü, bir derlemeye yalnızca bilgilendirme amacıyla ek sürüm bilgileri ekleyen bir dizedir; bu bilgi çalışma zamanında kullanılmaz. Metin tabanlı bilgilendirme sürümü, ürünün pazarlama belgelerine, paketlemesine veya ürün adına karşılık gelir ve çalışma zamanı tarafından kullanılmaz. Örneğin, bir bilgilendirme sürümü "Ortak Dil Çalışma Zamanı sürüm 1.0" veya "NET Control SP 2" olabilir. Microsoft Windows'daki dosya özellikleri iletişim kutusunun Sürüm sekmesinde, bu bilgi "Ürün Sürümü" öğesinde görünür.  
  
> [!NOTE]
> Herhangi bir metni ayarlayabilseniz de dize derleme sürüm numarası tarafından kullanılan biçimde değilse veya o biçimdeyse ancak jokerler içeriyorsa derleme esnasında bir uyarı iletisi görünür. Bu uyarı zararsız olur.  
  
Bilgilendirme sürümü <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType> özel özniteliği kullanılarak temsil edilir. Bilgilendirici sürüm özniteliği hakkında daha fazla bilgi için bkz. [derleme özniteliklerini ayarlama](set-attributes.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanının derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Uygulama yapılandırma](../../framework/configure-apps/index.md)
- [Derleme özniteliklerini ayarlama](set-attributes.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
