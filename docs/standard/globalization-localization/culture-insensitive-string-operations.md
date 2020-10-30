---
title: Kültüre Duyarsız Dize İşlemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, culture-insensitive string operations
- case-sensitive comparisons
- globalization [.NET], culture-insensitive string operations
- strings [.NET], culture-insensitive string operations
- localization [.NET], culture-insensitive string operations
- world-ready applications, culture-insensitive string operations
- culture-sensitive string operations
- culture-insensitive string operations
ms.assetid: e6e2bb94-a95d-44e2-b68c-cfdd1db77784
ms.openlocfilehash: 3a6085d15dbaa30144436b163a6ecb777698f4f1
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93064008"
---
# <a name="culture-insensitive-string-operations"></a>Kültüre duyarsız dize işlemleri

Kültüre özel dize işlemleri, kullanıcılara sonuçları kültüre göre görüntülemek üzere tasarlanmış uygulamalar oluşturuyorsanız bir avantaj olabilir. Varsayılan olarak, kültüre duyarlı yöntemler <xref:System.Globalization.CultureInfo.CurrentCulture%2A> geçerli iş parçacığının özelliğinden kullanılacak kültürü elde eder.

Bazen kültüre duyarlı dize işlemleri istenen davranış değildir. Sonuçların kültürden bağımsız olması gerektiğinde, kültüre duyarlı işlemleri kullanmak, uygulama kodunun, özel durum eşleştirmeleri ve sıralama kuralları içeren kültürlerde başarısız olmasına yol açabilir. Bir örnek için, [dizeler kullanmak Için En Iyi Yöntemler](../base-types/best-practices-strings.md) konusunun ["geçerli kültürü kullanan dize karşılaştırmaları"](../base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) bölümüne bakın.

Dize işlemlerinin kültüre duyarlı ya da kültüre duyarsız olması, uygulamanızın sonuçları nasıl kullandığına bağlıdır. Sonuçları kullanıcıya görüntüleyen dize işlemleri tipik olarak kültüre duyarlı olmalıdır. Örneğin, bir uygulama yerelleştirilmiş dizeleri sıralanmış bir listesini liste kutusunda görüntülerse, uygulamanın kültüre duyarlı sıralama gerçekleştirmesi gerekir.

Dahili olarak kullanılan dize işlemlerinin sonuçları tipik olarak kültüre duyarlı olmalıdır. Genellikle, uygulama dosya adlarıyla, kullanıcıya görüntülenmeyen kalıcılık biçimleriyle veya sembolik bilgilerle, dize işlemlerinin sonuçlarıyla çalışıyorsa kültür tarafından değiştirilmemelidir. Örneğin, bir uygulama tanınan bir XML etiketi olup olmadığını belirlemek için bir dizeyi karşılaştırırsa, karşılaştırma kültüre duyarlı olmamalıdır. Buna ek olarak, bir güvenlik kararı bir dize karşılaştırma veya örnek değişikliği işleminin sonucunu temel alıyorsa, sonucun değerinden etkilenmemesini sağlamak için işlem kültür duyarsız olmalıdır <xref:System.Globalization.CultureInfo.CurrentCulture%2A> .

Yerelleştirme ve genelleştirme sorunlarını işlemek için kod içeren bir uygulama geliştirirken, varsayılan olarak kültüre duyarlı sonuçları alan .NET yöntemlerinden haberdar olmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve yerelleştirme](index.md)
