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
ms.openlocfilehash: 06c46033936e16355b8d2eb6650e8731a04af6e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141279"
---
# <a name="culture-insensitive-string-operations"></a>Kültüre duyarsız dize işlemleri

Kültüre özel dize işlemleri, kullanıcılara sonuçları kültüre göre görüntülemek üzere tasarlanmış uygulamalar oluşturuyorsanız bir avantaj olabilir. Varsayılan olarak, kültüre duyarlı yöntemler geçerli iş parçacığının <xref:System.Globalization.CultureInfo.CurrentCulture%2A> özelliğinden kullanılacak kültürü elde eder.

Kültüre duyarlı dize işlemlerinin her zaman istenen davranış olmadığını unutmayın. Sonuçların kültürden bağımsız olması gerektiğinde, kültüre duyarlı işlemleri kullanmak, uygulama kodunun, özel durum eşleştirmeleri ve sıralama kuralları içeren kültürlerde başarısız olmasına yol açabilir. Bir örnek için, [dizeler kullanmak Için En Iyi Yöntemler](../../../docs/standard/base-types/best-practices-strings.md) konusunun ["geçerli kültürü kullanan dize karşılaştırmaları"](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) bölümüne bakın.

Dize işlemlerinin kültüre duyarlı ya da kültüre duyarsız olması, uygulamanızın sonuçları nasıl kullandığına bağlıdır. Sonuçları kullanıcıya görüntüleyen dize işlemleri tipik olarak kültüre duyarlı olmalıdır. Örneğin, bir uygulama yerelleştirilmiş dizeleri sıralanmış bir listesini liste kutusunda görüntülerse, uygulamanın kültüre duyarlı sıralama gerçekleştirmesi gerekir.

Dahili olarak kullanılan dize işlemlerinin sonuçları tipik olarak kültüre duyarlı olmalıdır. Genellikle, uygulama dosya adlarıyla, kullanıcıya görüntülenmeyen kalıcılık biçimleriyle veya sembolik bilgilerle, dize işlemlerinin sonuçlarıyla çalışıyorsa kültür tarafından değiştirilmemelidir. Örneğin, bir uygulama tanınan bir XML etiketi olup olmadığını belirlemek için bir dizeyi karşılaştırırsa, karşılaştırma kültüre duyarlı olmamalıdır. Buna ek olarak, bir güvenlik kararı bir dize karşılaştırma veya örnek değişikliği işleminin sonucunu temel alıyorsa, sonucun <xref:System.Globalization.CultureInfo.CurrentCulture%2A>değerinden etkilenmemesini sağlamak için işlem kültür duyarsız olmalıdır.

Yerelleştirme ve genelleştirme sorunlarını işlemek için kod içeren bir uygulama geliştiriyor olsanız da olmasanız da, varsayılan olarak kültüre duyarlı sonuçlar getiren .NET Framework yöntemlerinden haberdar olmanız gerekir. Bu konunun amacı kültüre duyarlı olmayan sonuçlar elde etmek üzere uygulamalarınızın bu yöntemleri kullanmasının doğru yolunu göstermektir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
