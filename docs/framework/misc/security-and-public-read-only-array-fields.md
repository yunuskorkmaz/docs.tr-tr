---
title: Güvenlik ve Genel Salt Okunur Dizi Alanları
description: Uygulamanızın sınır davranışını veya güvenliğini tanımlamak için ortak salt okuma dizisi alanlarını kullanmaktan kaçının.
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 5e499f8052306cd1ad063c9f44a2a0f1d0b365ef
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855744"
---
# <a name="security-and-public-read-only-array-fields"></a>Güvenlik ve Genel Salt Okunur Dizi Alanları

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Salt okuma genel dizi alanları değiştirilirken, uygulamanızın sınır davranışını veya güvenliğini tanımlamak için, yönetilen kitaplıklardan hiçbir şekilde salt okuma temelli dizi alanları kullanmayın.  
  
## <a name="remarks"></a>Açıklamalar  

Bazı .NET sınıfları, platforma özgü sınır parametreleri içeren salt okunurdur ortak alanları içerir. Örneğin, alan, <xref:System.IO.Path.InvalidPathChars> bir dosya yolu dizesinde izin verilmeyen karakterleri açıklayan bir dizidir. Birçok benzer alan .NET genelinde mevcuttur.  
  
 Gibi genel salt okuma alanlarının değerleri, kodunuzun <xref:System.IO.Path.InvalidPathChars> uygulama etki alanını paylaşan kodunuz veya kodunuz tarafından değiştirilebilir.  Uygulamalarınızın sınır davranışını tanımlamak için bu gibi salt okunurdur genel dizi alanlarını kullanmamalısınız.  Bunu yaparsanız, kötü amaçlı kod sınır tanımlarını değiştirebilir ve kodunuzu beklenmedik yollarla kullanabilir.  
  
 Sürüm 2,0 ve .NET Framework üzeri sürümlerde, genel dizi alanlarını kullanmak yerine yeni bir dizi döndüren yöntemleri kullanmanız gerekir.  Örneğin, alanını kullanmak yerine <xref:System.IO.Path.InvalidPathChars> yöntemini kullanmanız gerekir <xref:System.IO.Path.GetInvalidPathChars%2A> .  
  
 .NET Framework türlerin, sınır türlerini dahili olarak tanımlamak için ortak alanları kullanmadığını unutmayın.  Bunun yerine, .NET Framework ayrı özel alanlar kullanır.  Bu ortak alanların değerlerinin değiştirilmesi .NET Framework türlerinin davranışını değiştirmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
