---
title: Devralma Desteği
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 668f4f1dd284550e644ce6b8a4491ca47105575e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230921"
---
# <a name="inheritance-support"></a>Devralma Desteği
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekleyen *tek tablo eşleme*. Diğer bir deyişle, tam devralma hiyerarşisinde bir tek veritabanı tablosunda depolanır. Tablo, hiyerarşinin tamamı için tüm olası veri sütunları düzleştirilmiş birleşimini içerir. (Bir birleşim özgün tablolardan birini mevcut satırları içeren bir tabloya iki tabloyu birleştirerek sonucudur.) Her satır, satır tarafından temsil edilen örneği türü için geçerli olmayan sütunlardaki null değerlere sahiptir.  
  
 Tek tablo eşleme stratejisi basit devralma gösterimi ve birçok farklı türdeki sorgular için iyi bir performans özellikleri sağlar.  
  
 Bu eşleme içinde uygulamak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], devralma hiyerarşisi kök sınıfında öznitelik özellikleri ve öznitelikler belirtmeniz gerekir. Daha fazla bilgi için [nasıl yapılır: Devralma hiyerarşilerini eşleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
 Visual Studio kullanan geliştiricilerin de kullanabilir [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] devralma hiyerarşilerini eşleme için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
