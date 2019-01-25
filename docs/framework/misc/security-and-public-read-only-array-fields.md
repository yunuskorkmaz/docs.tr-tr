---
title: Güvenlik ve Genel Salt Okunur Dizi Alanları
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03f3ce51eaab9e08d5f05932d9360adc4fd2110f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560999"
---
# <a name="security-and-public-read-only-array-fields"></a>Güvenlik ve Genel Salt Okunur Dizi Alanları
Hiçbir zaman salt okunur genel dizi alanları salt okunur genel dizi alanları değiştirilebilir uygulamalarınızın güvenliği ve sınır davranışını tanımlamak için yönetilen kitaplıklarından kullanın.  
  
## <a name="remarks"></a>Açıklamalar  
 Bazı .NET framework sınıfları, platforma özgü sınır parametreleri içeren salt okunur ortak alanları içerir.  Örneğin, <xref:System.IO.Path.InvalidPathChars> dosya yol dizesi izin verilmeyen karakterler tanımlayan bir dizi bir alandır.  Pek çok benzer alanları, .NET Framework'de yok.  
  
 Genel salt okunur alanların değerlerini ister <xref:System.IO.Path.InvalidPathChars> kodunuzu veya kodunuzun uygulama etki alanını paylaşan kod tarafından değiştirilebilir.  Uygulamalarınızı sınır davranışını tanımlamak için salt okunur genel dizi alanları böyle kullanmamanız gerekir.  Bunu yaparsanız, kötü amaçlı kod sınır tanımları alter ve kodunuzu beklenmedik bir şekilde kullanın.  
  
 Sürüm 2.0 ve daha sonra .NET Framework, ortak bir dizi alanları kullanmak yerine yeni bir dizi döndüren yöntemler kullanmanız gerekir.  Örneğin, kullanmak yerine <xref:System.IO.Path.InvalidPathChars> alan kullanmalıdır <xref:System.IO.Path.GetInvalidPathChars%2A> yöntemi.  
  
 .NET Framework türleri genel alanlar dahili olarak sınır türleri tanımlamak için kullanmamanız unutmayın.  Bunun yerine, .NET Framework ayrı özel alanları kullanır.  Bu genel alanların değerlerini değiştirme, .NET Framework türleri davranışını değiştirmez.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
