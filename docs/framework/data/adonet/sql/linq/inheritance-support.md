---
title: Devralma Desteği
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 7673e69458d5c1af854747c43ba463332a9cd588
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158259"
---
# <a name="inheritance-support"></a>Devralma Desteği

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]*tek tablo eşlemeyi*destekler. Diğer bir deyişle, tüm devralma hiyerarşisi tek bir veritabanı tablosunda depolanır. Tablo, tüm hiyerarşinin tüm olası veri sütunlarının düzleştirilmiş birleşimini içerir. (UNION, iki tablonun, özgün tablolardan birinde bulunan satırları içeren tek bir tabloda birleştirilmesinin sonucudur.) Her satırda, satır tarafından temsil edilen örneğin türüne uygulanmayan sütunlarda null değerler vardır.  
  
 Tek tablo eşleme stratejisi, devralmanın en basit gösterimidir ve birçok farklı sorgu kategorisi için iyi performans özellikleri sağlar.  
  
 Bu eşlemeyi ' de uygulamak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Devralma hiyerarşisinin kök sınıfında öznitelikleri ve öznitelik özelliklerini belirtmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: harita devralma hiyerarşileri](how-to-map-inheritance-hierarchies.md).  
  
 Visual Studio kullanan geliştiriciler, devralma hiyerarşileri eşlemek için Nesne İlişkisel Tasarımcısı da kullanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
