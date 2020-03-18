---
title: Uydu montaj yükleme algoritması - .NET Core
description: .NET Core'da Uydu montaj yükleme algoritmasının ayrıntılarının açıklaması
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70105314"
---
# <a name="satellite-assembly-loading-algorithm"></a>Uydu montaj yükleme algoritması

Uydu derlemeleri, dil ve kültür için özelleştirilmiş yerelleştirilmiş kaynakları depolamak için kullanılır.

Uydu derlemeleri genel yönetilen derlemelerden farklı bir yükleme algoritması kullanır.

## <a name="when-are-satellite-assemblies-loaded"></a>Uydu meclisleri ne zaman yüklenir?

Yerelleştirilmiş bir kaynak yüklenirken uydu derlemeleri yüklenir.

Yerelleştirilmiş kaynakları yüklemek için temel <xref:System.Resources.ResourceManager?displayProperty=fullName> API sınıftır. Sonuçta <xref:System.Resources.ResourceManager> sınıf her <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>biri için yöntem çağırır.

Üst düzey API'ler alt düzey API'yi özetleyebilir.

## <a name="algorithm"></a>Algoritma

.NET Core kaynak geri dönüş işlemi aşağıdaki adımları içerir:

1. Örneği `active` <xref:System.Runtime.Loader.AssemblyLoadContext> belirleyin. Her durumda, `active` örneğin yürütme derlemesi. <xref:System.Runtime.Loader.AssemblyLoadContext>

2. Örnek, `active` istenen kültür için bir uydu tertibatını öncelik sırasına göre yüklemeye çalışır:
    - Önbelleğini kontrol ediyorum.
    - İstenilenle <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> eşleşen bir alt dizini (örneğin) `es-MX`için şu anda çalıştırılan derlemenin dizinini denetleme.

        > [!NOTE]
        > Bu özellik 3.0'dan önce .NET Core'da uygulanmadı.
        >
        > [!NOTE]
        > Linux ve macOS'ta, alt dizini büyük/küçük harf duyarlıdır ve aşağıdakilerden biri olmalıdır:
        > - Kesinlikle uygun durumda.
        > - Küçük harfli ol.

    - Örnek ise, [varsayılan uydu (kaynak) derleme sondalama](default-probing.md#satellite-resource-assembly-probing) mantığı çalıştırarak. `active` <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>

    - <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> İşlevi çağırıyor.

    - Olayı <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> yükseltiyor.

    - Olayı <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> yükseltiyor.

3. Uydu montajı yüklenirse:
   - Olay <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> yükseltilir.
   - Derleme istenen kaynak için aranır. Çalışma zamanı, derlemedeki kaynağı bulursa, onu kullanır. Kaynağı bulamazsa, aramaya devam ediyor.

    > [!NOTE]
    > Uydu derlemesi içinde bir kaynak bulmak <xref:System.Resources.ResourceManager> için, çalışma zamanı geçerli <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>için istenen kaynak dosyası için arar. Kaynak dosyası içinde, istenen kaynak adını arar. Ya bulunamazsa, kaynak bulunamadı olarak kabul edilir.

4. Çalışma zamanı sonraki birçok potansiyel düzeyleri üzerinden ana kültür derlemeleri arar, her zaman adımları 2 & 3 yinelenen.

    Her kültürün <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> yalnızca bir üst öğesi vardır ve bu özellik tarafından tanımlanır.

    Bir kültürün <xref:System.Globalization.CultureInfo.Parent%2A> özelliği <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>olduğunda ana kültürleri arama durur.

    <xref:System.Globalization.CultureInfo.InvariantCulture>Için, biz adım 2 & 3 dönmek değil, daha ziyade adım 5 ile devam edin.

5. Kaynak hala bulunamazsa, varsayılan (geri dönüş) kültürü için kaynak kullanılır.

   Genellikle, varsayılan kültür için kaynaklar ana uygulama derlemesi dahildir. Ancak, <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> özellik <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> için belirtebilirsiniz. Bu değer, kaynaklar için nihai geri dönüş konumunun ana derleme yerine uydu derlemesi olduğunu gösterir.

    > [!NOTE]
    > Varsayılan kültür nihai geri dönüş. Bu nedenle, varsayılan kaynak dosyasına her zaman kapsamlı bir kaynak kümesi eklemenizi öneririz. Bu, özel durumların atılmasını önlemeye yardımcı olur. Ayrıntılı bir kümeye sahip olarak, tüm kaynaklar için bir geri dönüş sağlar ve kültürel olarak özel olmasa bile, kullanıcı için her zaman en az bir kaynağın bulunduğundan emin olursunuz.

6. Sonunda
   - Çalışma süresi varsayılan (geri dönüş) kültürü için bir kaynak dosyası <xref:System.Resources.MissingManifestResourceException> <xref:System.Resources.MissingSatelliteAssemblyException> bulamazsa, bir veya özel durum atılır.
   - Kaynak dosyası bulunurancak istenen kaynak yoksa, istek döndürür. `null`
