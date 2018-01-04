---
title: "Kültüre Duyarsız Dize İşlemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 697d3ec32af6b704fbb1787bbb9ba1de57a0632e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="culture-insensitive-string-operations"></a>Kültüre Duyarsız Dize İşlemleri
Kültüre özel dize işlemleri, kullanıcılara sonuçları kültüre göre görüntülemek üzere tasarlanmış uygulamalar oluşturuyorsanız bir avantaj olabilir. Varsayılan olarak, aşağıdakiler arasından kullanılacak kültürü kültüre duyarlı yöntemleri elde <xref:System.Globalization.CultureInfo.CurrentCulture%2A> özelliği için geçerli iş parçacığının.  
  
 Kültüre duyarlı dize işlemlerinin her zaman istenen davranış olmadığını unutmayın. Sonuçların kültürden bağımsız olması gerektiğinde, kültüre duyarlı işlemleri kullanmak, uygulama kodunun, özel durum eşleştirmeleri ve sıralama kuralları içeren kültürlerde başarısız olmasına yol açabilir. Örneğin, "Dize karşılaştırmaları kullanma geçerli kültür" bölümüne bakın [kullanarak dizeleri için en iyi uygulamaları](../../../docs/standard/base-types/best-practices-strings.md) makalesi.  
  
 Dize işlemlerinin kültüre duyarlı ya da kültüre duyarsız olması, uygulamanızın sonuçları nasıl kullandığına bağlıdır. Sonuçları kullanıcıya görüntüleyen dize işlemleri tipik olarak kültüre duyarlı olmalıdır. Örneğin, bir uygulama yerelleştirilmiş dizeleri sıralanmış bir listesini liste kutusunda görüntülerse, uygulamanın kültüre duyarlı sıralama gerçekleştirmesi gerekir.  
  
 Dahili olarak kullanılan dize işlemlerinin sonuçları tipik olarak kültüre duyarlı olmalıdır. Genellikle, uygulama dosya adlarıyla, kullanıcıya görüntülenmeyen kalıcılık biçimleriyle veya sembolik bilgilerle, dize işlemlerinin sonuçlarıyla çalışıyorsa kültür tarafından değiştirilmemelidir. Örneğin, bir uygulama tanınan bir XML etiketi olup olmadığını belirlemek için bir dizeyi karşılaştırırsa, karşılaştırma kültüre duyarlı olmamalıdır. Dize karşılaştırma ya da durum değişiklik işlemi sonucu üzerinde bir güvenlik karar temel alıyorsa, ayrıca, işlemi kültüre sonuç değeri olarak etkilenmediğinden emin olmak için duyarsız olmalıdır <xref:System.Globalization.CultureInfo.CurrentCulture%2A>.  
  
 Yerelleştirme ve genelleştirme sorunlarını işlemek için kod içeren bir uygulama geliştiriyor olsanız da olmasanız da, varsayılan olarak kültüre duyarlı sonuçlar getiren .NET Framework yöntemlerinden haberdar olmanız gerekir. Bu konunun amacı kültüre duyarlı olmayan sonuçlar elde etmek üzere uygulamalarınızın bu yöntemleri kullanmasının doğru yolunu göstermektir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
