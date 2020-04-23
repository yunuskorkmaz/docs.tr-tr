---
title: XAML Güvenlik Konuları
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: 1864910b339c74e3033fb4d6d8baebffada1a4f8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071691"
---
# <a name="xaml-security-considerations"></a>XAML güvenlik konuları

Bu makalede, XAML ve .NET XAML Hizmetleri API kullandığınızda uygulamalarda güvenlik için en iyi uygulamaları açıklanır.

## <a name="untrusted-xaml-in-applications"></a>Uygulamalarda Güvenilmeyen XAML

En genel anlamda, güvenilmeyen XAML, uygulamanızın özellikle içermediği veya yayan herhangi bir XAML kaynağıdır.

Güvenilir ve imzalı bir `resx`derleme içinde derlenen veya -türü kaynak olarak depolanan XAML doğal olarak güvenilmez değildir. XAML'ye bir bütün olarak derlemeye güvendiğiniz kadar güvenebilirsiniz. Çoğu durumda, yalnızca bir akıştan veya başka bir G/Ç'den yüklediğiniz bir XAML kaynağı olan gevşek XAML'nin güven yönleri yle ilgilenirsiniz. Gevşek XAML, dağıtım ve paketleme altyapısına sahip bir uygulama modelinin belirli bir bileşeni veya özelliği değildir. Ancak, bir derleme gevşek XAML yükleme içeren bir davranış uygulayabilirsiniz.

Güvenilmeyen XAML için, genellikle güvenilmeyen kod gibi aynı tedavi etmelidir. Güvenilmeyen XAML'nin güvenilen kodunuza erişmesini önlemek için kum kutulama veya diğer metaforları kullanın.

XAML özelliklerinin doğası, XAML'ye nesneleri oluşturma ve özelliklerini ayarlama hakkı verir. Bu özellikler, tür dönüştürücülere erişme, uygulama etki alanında eşleme ve derlemelere `x:Code` erişim, biçimlendirme uzantıları, bloklar ve benzeri kullanarak da içerir.

XAML, dil düzeyi özelliklerine ek olarak birçok teknolojide UI tanımı için kullanılır. Güvenilmeyen XAML'nin yüklenmesi, kötü amaçlı bir sahte iI yükleme anlamına gelebilir.

## <a name="sharing-context-between-readers-and-writers"></a>Okuyucular ve Yazarlar Arasında Bağlam Paylaşımı

XAML okuyucuları ve XAML yazarları için .NET XAML Hizmetleri mimarisi genellikle bir XAML okuyucusunun XAML yazarına veya paylaşılan bir XAML şema bağlamında paylaşılmasını gerektirir. XAML düğüm döngü mantığı yazıyorsanız veya özel bir kaydetme yolu sağlıyorsanız nesneleri veya bağlamları paylaşmak gerekebilir. XAML okuyucu örneklerini, varsayılan olmayan XAML şema bağlamLarını veya XAML okuyucu/yazar sınıfları ayarlarını güvenilir ve güvenilmeyen kod arasında paylaşmayın.

CLR tabanlı bir tür desteği için XAML nesne yazma içeren çoğu senaryo ve işlem yalnızca varsayılan XAML şema bağlamı kullanabilirsiniz. Varsayılan XAML şema bağlamı, tam güveni tehlikeye atabilecek ayarları açıkça içermez. Bu nedenle, güvenilir ve güvenilmeyen XAML okuyucu/yazar bileşenleri arasında bağlam paylaşmak güvenlidir. Ancak, bunu yaparsanız, yine de bu tür okuyucuları ve <xref:System.AppDomain> yazarları ayrı kapsamlarda tutmak için en iyi uygulamadır, bunlardan biri özellikle tasarlanmış / kısmi güven için kumkutulu.

## <a name="xaml-namespaces-and-assembly-trust"></a>XAML İsim Alanları ve Derleme Güveni

XAML'nin özel bir XAML ad alanı eşlemini derlemeye nasıl yorumladığına yönelik temel niteliksiz sözdizimi ve tanımı, uygulama etki alanına yüklenen güvenilir ve güvenilmeyen derleme yi ayırt etmez. Bu nedenle, güvenilir bir derlemenin amaçlanan XAML ad alanı eşlemini taklit etmek ve bir XAML kaynağının bildirilen nesne ve özellik bilgilerini yakalamak için güvenilir olmayan bir derleme teknik olarak mümkündür. Bu durumu önlemek için güvenlik gereksinimleriniz varsa, amaçlanan XAML ad alanı eşleme aşağıdaki tekniklerden biri kullanılarak yapılmalıdır:

- Uygulamanızın XAML'si tarafından yapılan herhangi bir XAML ad alanı eşlemesinde güçlü bir ada sahip tam nitelikli bir montaj adı kullanın.

- XAML okuyucularınız ve XAML nesne yazarlarınız <xref:System.Xaml.XamlSchemaContext> için belirli bir oluşturma yaparak, montaj eşlemesi sabit bir başvuru derlemeleri kümesiyle sınırlandırın. Bkz. <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.

## <a name="xaml-type-mapping-and-type-system-access"></a>XAML Tip Haritalama ve Tip Sistem Erişimi

XAML, clr'in temel CLR türü sistemini nasıl uyguladığına birçok yönden bir eş olan kendi tip sistemini destekler. Ancak, tür bilgilerine dayalı bir tür hakkında güven kararları aldığınız tür farkındalığının belirli yönleri için, CLR destek türlerindeki tür bilgilerine ertelemelisiniz. Bunun nedeni, XAML türü sistemin belirli raporlama özelliklerinden bazılarının sanal yöntemler olarak açık bırakılması ve bu nedenle orijinal .NET XAML Hizmetleri uygulamalarının tam denetimi altında olmamasıdır. XAML türü sistemi genişletilebilir olduğundan bu genişletilebilirlik noktaları vardır, XAML kendisi genişletilebilirlik ve varsayılan CLR destekli uygulama ve varsayılan XAML şema bağlamı karşı olası alternatif tür eşleme stratejileri maç. Daha fazla bilgi için, <xref:System.Xaml.XamlType> <xref:System.Xaml.XamlMember>ve. özelliklerinin birkaçı hakkında belirli notlar bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xaml.Permissions.XamlAccessLevel>
