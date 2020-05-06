---
title: Uydu derleme yükleme algoritması-.NET Core
description: .NET Core 'da uydu derleme yükleme algoritmasının ayrıntılarının açıklaması
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 17f29a9aca79019daa91736e586bf1b6b753a9ec
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859523"
---
# <a name="satellite-assembly-loading-algorithm"></a>Uydu derleme yükleme algoritması

Uydu derlemeleri, dil ve kültür için özelleştirilmiş yerelleştirilmiş kaynakları depolamak için kullanılır.

Uydu derlemeleri genel yönetilen derlemelerden farklı bir yükleme algoritması kullanır.

## <a name="when-are-satellite-assemblies-loaded"></a>Uydu derlemeleri ne zaman yüklenir?

Bir yerelleştirilmiş kaynak yüklenirken uydu derlemeleri yüklenir.

Yerelleştirilmiş kaynakları yüklemek için temel API, <xref:System.Resources.ResourceManager?displayProperty=fullName> sınıfındır. Sonuç olarak <xref:System.Resources.ResourceManager> , sınıf her biri <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>için yöntemini çağırır.

Üst düzey API 'Ler alt düzey API 'YI soyut olabilir.

## <a name="algorithm"></a>Algoritma

.NET Core kaynak geri dönüş işlemi aşağıdaki adımları içerir:

1. `active` <xref:System.Runtime.Loader.AssemblyLoadContext> Her durumda, `active` örnek yürüten derleme ' dir <xref:System.Runtime.Loader.AssemblyLoadContext>.

2. Örnek `active` , istenen kültür için şu kadar bir uydu derlemesini yüklemeye çalışır:
    - Önbelleği denetleniyor.
    - İstenen <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (örneğin `es-MX`) bir alt dizin için şu anda yürütülmekte olan derlemenin dizini denetleniyor.

        > [!NOTE]
        > Bu özellik 3,0 öncesi .NET Core 'da uygulanmadı.
        >
        > [!NOTE]
        > Linux ve macOS 'ta alt dizin büyük/küçük harfe duyarlıdır ve şunlardan biri olmalıdır:
        >
        > - Büyük/küçük harf eşleştir.
        > - Küçük bir durumda olun.

    - Örnek ise, [varsayılan uydu (kaynak) derleme yoklama](default-probing.md#satellite-resource-assembly-probing) mantığını çalıştırarak. `active` <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>

    - <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> İşlevi çağrılıyor.

    - <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> Olayı oluşturma.

    - <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> Olayı oluşturma.

3. Bir uydu derlemesi yüklüyse:
   - <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> Olay tetiklenir.
   - Derleme, istenen kaynak için arandı. Çalışma zamanı derlemede kaynağı bulursa, onu kullanır. Kaynak bulamazsa, aramaya devam eder.

    > [!NOTE]
    > Uydu derlemesi içindeki bir kaynağı bulmak için, çalışma zamanı, <xref:System.Resources.ResourceManager> için tarafından istenen kaynak dosyasını arar. <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> Kaynak dosyasında, istenen kaynak adını arar. Herhangi biri bulunmazsa, kaynak bulunamadı olarak kabul edilir.

4. Daha sonra çalışma zamanı, ana kültür derlemelerini birçok olası düzey aracılığıyla arar, her zaman 2 & 3. adımları tekrarlayarak.

    Her kültürün, <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> özelliği tarafından tanımlanan yalnızca bir üst öğesi vardır.

    Bir kültürün <xref:System.Globalization.CultureInfo.Parent%2A> özelliği olduğunda üst kültürleri için arama işlemi <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>duraklar.

    <xref:System.Globalization.CultureInfo.InvariantCulture>İçin adım 2 & 3 ' e dönmedik, ancak 5. adıma geçin.

5. Kaynak hala bulunamazsa, varsayılan (geri dönüş) kültürün kaynağı kullanılır.

   Genellikle, varsayılan kültür için kaynaklar ana uygulama derlemesine dahil edilmiştir. Ancak, <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> özelliği için belirtebilirsiniz <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> . Bu değer, kaynaklar için en son geri dönüş konumunun ana derleme yerine bir uydu derlemesi olduğunu gösterir.

    > [!NOTE]
    > Varsayılan kültür en son geri dönüş olur. Bu nedenle, varsayılan kaynak dosyasına her zaman kapsamlı bir kaynak kümesini dahil etmenizi öneririz. Bu, özel durumların oluşmasını önlemeye yardımcı olur. Geniş kapsamlı bir küme sunarak, tüm kaynaklar için bir geri dönüş sağlarsınız ve Kullanıcı için en az bir kaynağın, önemli ölçüde spesifik olmasa bile her zaman mevcut olduğundan emin olursunuz.

6. Son olarak
   - Çalışma zamanı varsayılan (geri dönüş) kültürü için bir kaynak dosyası bulamazsa, <xref:System.Resources.MissingManifestResourceException> veya <xref:System.Resources.MissingSatelliteAssemblyException> özel durumu oluşturulur.
   - Kaynak dosyası bulunursa ancak istenen kaynak yoksa istek geri döner `null`.
