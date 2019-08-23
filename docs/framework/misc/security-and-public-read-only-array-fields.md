---
title: Güvenlik ve Genel Salt Okunur Dizi Alanları
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d36009fa4fc7b9299708768fe34a75f1fde6797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910731"
---
# <a name="security-and-public-read-only-array-fields"></a>Güvenlik ve Genel Salt Okunur Dizi Alanları
Salt okuma genel dizi alanları değiştirilirken, uygulamanızın sınır davranışını veya güvenliğini tanımlamak için, yönetilen kitaplıklardan hiçbir şekilde salt okuma temelli dizi alanları kullanmayın.  
  
## <a name="remarks"></a>Açıklamalar  
 Bazı .NET Framework sınıfları, platforma özgü sınır parametreleri içeren salt okunurdur ortak alanları içerir.  Örneğin, <xref:System.IO.Path.InvalidPathChars> alan, bir dosya yolu dizesinde izin verilmeyen karakterleri açıklayan bir dizidir.  .NET Framework boyunca birçok benzer alan mevcuttur.  
  
 Gibi <xref:System.IO.Path.InvalidPathChars> genel salt okuma alanlarının değerleri, kodunuzun uygulama etki alanını paylaşan kodunuz veya kodunuz tarafından değiştirilebilir.  Uygulamalarınızın sınır davranışını tanımlamak için bu gibi salt okunurdur genel dizi alanlarını kullanmamalısınız.  Bunu yaparsanız, kötü amaçlı kod sınır tanımlarını değiştirebilir ve kodunuzu beklenmedik yollarla kullanabilir.  
  
 Sürüm 2,0 ve .NET Framework üzeri sürümlerde, genel dizi alanlarını kullanmak yerine yeni bir dizi döndüren yöntemleri kullanmanız gerekir.  Örneğin, <xref:System.IO.Path.InvalidPathChars> alanını kullanmak yerine <xref:System.IO.Path.GetInvalidPathChars%2A> yöntemini kullanmanız gerekir.  
  
 .NET Framework türlerin, sınır türlerini dahili olarak tanımlamak için ortak alanları kullanmadığını unutmayın.  Bunun yerine, .NET Framework ayrı özel alanlar kullanır.  Bu ortak alanların değerlerinin değiştirilmesi .NET Framework türlerinin davranışını değiştirmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
