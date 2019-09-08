---
title: Devralma Desteği
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 034aa6e75ca304d98aa4d3e1f3023c1a6940b73c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781559"
---
# <a name="inheritance-support"></a>Devralma Desteği
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]*tek tablo eşlemeyi*destekler. Diğer bir deyişle, tüm devralma hiyerarşisi tek bir veritabanı tablosunda depolanır. Tablo, tüm hiyerarşinin tüm olası veri sütunlarının düzleştirilmiş birleşimini içerir. (UNION, iki tablonun, özgün tablolardan birinde bulunan satırları içeren tek bir tabloda birleştirilmesinin sonucudur.) Her satırda, satır tarafından temsil edilen örneğin türüne uygulanmayan sütunlarda null değerler vardır.  
  
 Tek tablo eşleme stratejisi, devralmanın en basit gösterimidir ve birçok farklı sorgu kategorisi için iyi performans özellikleri sağlar.  
  
 Bu eşlemeyi ' de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]uygulamak için devralma hiyerarşisinin kök sınıfında öznitelikleri ve öznitelik özelliklerini belirtmeniz gerekir. Daha fazla bilgi için [nasıl yapılır: Harita devralma hiyerarşileri](how-to-map-inheritance-hierarchies.md).  
  
 Visual Studio kullanan geliştiriciler, devralma hiyerarşileri eşlemek için Nesne İlişkisel Tasarımcısı da kullanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
