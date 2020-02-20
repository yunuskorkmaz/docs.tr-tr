---
title: Güvenlik ve Genel Salt Okunur Dizi Alanları
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 2df4acc0606e4fe8fccee4a8acc6ab744dcbbb71
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452714"
---
# <a name="security-and-public-read-only-array-fields"></a>Güvenlik ve Genel Salt Okunur Dizi Alanları
Salt okuma genel dizi alanları değiştirilirken, uygulamanızın sınır davranışını veya güvenliğini tanımlamak için, yönetilen kitaplıklardan hiçbir şekilde salt okuma temelli dizi alanları kullanmayın.  
  
## <a name="remarks"></a>Açıklamalar  

Bazı .NET sınıfları, platforma özgü sınır parametreleri içeren salt okunurdur ortak alanları içerir. Örneğin, <xref:System.IO.Path.InvalidPathChars> alanı bir dosya yolu dizesinde izin verilmeyen karakterleri açıklayan bir dizidir. Birçok benzer alan .NET genelinde mevcuttur.  
  
 <xref:System.IO.Path.InvalidPathChars> gibi genel salt okuma alanlarının değerleri, kodunuzun uygulama etki alanını paylaşan kodunuz veya kodunuz tarafından değiştirilebilir.  Uygulamalarınızın sınır davranışını tanımlamak için bu gibi salt okunurdur genel dizi alanlarını kullanmamalısınız.  Bunu yaparsanız, kötü amaçlı kod sınır tanımlarını değiştirebilir ve kodunuzu beklenmedik yollarla kullanabilir.  
  
 Sürüm 2,0 ve .NET Framework üzeri sürümlerde, genel dizi alanlarını kullanmak yerine yeni bir dizi döndüren yöntemleri kullanmanız gerekir.  Örneğin, <xref:System.IO.Path.InvalidPathChars> alanı kullanmak yerine <xref:System.IO.Path.GetInvalidPathChars%2A> yöntemini kullanmanız gerekir.  
  
 .NET Framework türlerin, sınır türlerini dahili olarak tanımlamak için ortak alanları kullanmadığını unutmayın.  Bunun yerine, .NET Framework ayrı özel alanlar kullanır.  Bu ortak alanların değerlerinin değiştirilmesi .NET Framework türlerinin davranışını değiştirmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
