---
title: Kültüre Duyarsız Dize İşlemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, culture-insensitive string operations
- case-sensitive comparisons
- globalization [.NET Framework], culture-insensitive string operations
- strings [.NET Framework], culture-insensitive string operations
- localization [.NET Framework], culture-insensitive string operations
- world-ready applications, culture-insensitive string operations
- culture-sensitive string operations
- culture-insensitive string operations
ms.assetid: e6e2bb94-a95d-44e2-b68c-cfdd1db77784
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7ca35f73590f8a7c58a0044136c05f341796dfc
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441664"
---
# <a name="culture-insensitive-string-operations"></a>Kültüre duyarsız dize işlemleri

Kültüre özel dize işlemleri, kullanıcılara sonuçları kültüre göre görüntülemek üzere tasarlanmış uygulamalar oluşturuyorsanız bir avantaj olabilir. Varsayılan olarak, kültüre duyarlı yöntemler kültürü kullanmak için elde <xref:System.Globalization.CultureInfo.CurrentCulture%2A> özelliği için geçerli iş parçacığı.

Kültüre duyarlı dize işlemlerinin her zaman istenen davranış olmadığını unutmayın. Sonuçların kültürden bağımsız olması gerektiğinde, kültüre duyarlı işlemleri kullanmak, uygulama kodunun, özel durum eşleştirmeleri ve sıralama kuralları içeren kültürlerde başarısız olmasına yol açabilir. Bir örnek için bkz. ["Dize karşılaştırmaları geçerli kültürü kullanan"](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) konusundaki [kullanarak dizeleri için en iyi](../../../docs/standard/base-types/best-practices-strings.md) makalesi.

Dize işlemlerinin kültüre duyarlı ya da kültüre duyarsız olması, uygulamanızın sonuçları nasıl kullandığına bağlıdır. Sonuçları kullanıcıya görüntüleyen dize işlemleri tipik olarak kültüre duyarlı olmalıdır. Örneğin, bir uygulama yerelleştirilmiş dizeleri sıralanmış bir listesini liste kutusunda görüntülerse, uygulamanın kültüre duyarlı sıralama gerçekleştirmesi gerekir.

Dahili olarak kullanılan dize işlemlerinin sonuçları tipik olarak kültüre duyarlı olmalıdır. Genellikle, uygulama dosya adlarıyla, kullanıcıya görüntülenmeyen kalıcılık biçimleriyle veya sembolik bilgilerle, dize işlemlerinin sonuçlarıyla çalışıyorsa kültür tarafından değiştirilmemelidir. Örneğin, bir uygulama tanınan bir XML etiketi olup olmadığını belirlemek için bir dizeyi karşılaştırırsa, karşılaştırma kültüre duyarlı olmamalıdır. Bir güvenlik kararı bir dize karşılaştırma veya harf değiştirme işlemi sonuçlarına alıyorsa, ayrıca, işlemi kültür-sonucu değerinden etkilenmemesini sağlamak için duyarlı olmalıdır <xref:System.Globalization.CultureInfo.CurrentCulture%2A>.

Yerelleştirme ve genelleştirme sorunlarını işlemek için kod içeren bir uygulama geliştiriyor olsanız da olmasanız da, varsayılan olarak kültüre duyarlı sonuçlar getiren .NET Framework yöntemlerinden haberdar olmanız gerekir. Bu konunun amacı kültüre duyarlı olmayan sonuçlar elde etmek üzere uygulamalarınızın bu yöntemleri kullanmasının doğru yolunu göstermektir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
