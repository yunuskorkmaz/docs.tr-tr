---
description: 'Daha fazla bilgi edinin: devralma desteği'
title: Devralma Desteği
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: ff6956441ab72f720151e42bd9358c8df1170e09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803873"
---
# <a name="inheritance-support"></a>Devralma Desteği

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]*tek tablo eşlemeyi* destekler. Diğer bir deyişle, tüm devralma hiyerarşisi tek bir veritabanı tablosunda depolanır. Tablo, tüm hiyerarşinin tüm olası veri sütunlarının düzleştirilmiş birleşimini içerir. (UNION, iki tablonun, özgün tablolardan birinde bulunan satırları içeren tek bir tabloda birleştirilmesinin sonucudur.) Her satırda, satır tarafından temsil edilen örneğin türüne uygulanmayan sütunlarda null değerler vardır.  
  
 Tek tablo eşleme stratejisi, devralmanın en basit gösterimidir ve birçok farklı sorgu kategorisi için iyi performans özellikleri sağlar.  
  
 Bu eşlemeyi ' de uygulamak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Devralma hiyerarşisinin kök sınıfında öznitelikleri ve öznitelik özelliklerini belirtmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: harita devralma hiyerarşileri](how-to-map-inheritance-hierarchies.md).  
  
 Visual Studio kullanan geliştiriciler, devralma hiyerarşileri eşlemek için Nesne İlişkisel Tasarımcısı da kullanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
