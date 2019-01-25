---
title: Devralma desteği
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 791cc68ce89ad8e56b8feeebe6bf84434c3e89c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692684"
---
# <a name="inheritance-support"></a>Devralma desteği
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekleyen *tek tablo eşleme*. Diğer bir deyişle, tam devralma hiyerarşisinde bir tek veritabanı tablosunda depolanır. Tablo, hiyerarşinin tamamı için tüm olası veri sütunları düzleştirilmiş birleşimini içerir. (Bir birleşim özgün tablolardan birini mevcut satırları içeren bir tabloya iki tabloyu birleştirerek sonucudur.) Her satır, satır tarafından temsil edilen örneği türü için geçerli olmayan sütunlardaki null değerlere sahiptir.  
  
 Tek tablo eşleme stratejisi basit devralma gösterimi ve birçok farklı türdeki sorgular için iyi bir performans özellikleri sağlar.  
  
 Bu eşleme içinde uygulamak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], devralma hiyerarşisi kök sınıfında öznitelik özellikleri ve öznitelikler belirtmeniz gerekir. Daha fazla bilgi için [nasıl yapılır: Devralma hiyerarşilerini eşleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
 Visual Studio kullanan geliştiricilerin de kullanabilir [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] devralma hiyerarşilerini eşleme için.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
