---
title: "Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan ve Alma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
ms.openlocfilehash: 5501e108d1866fc1ae6fc66f9fe665b63373414b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818641"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan ve Alma
Bu örnek, bir <xref:System.Collections.Concurrent.BlockingCollection%601> engelleme ve engellenmeyen bir şekilde içindeki öğesinden öğe ekleme ve kaldırma işlemlerinin nasıl yapılacağını gösterir. Hakkında daha fazla bilgi için <xref:System.Collections.Concurrent.BlockingCollection%601> bkz. [BlockingCollection genel bakış](blockingcollection-overview.md).  
  
 <xref:System.Collections.Concurrent.BlockingCollection%601>Boş olana kadar bir veya daha fazla öğe eklenene kadar nasıl numaralandırılacağını gösteren bir örnek için bkz. [nasıl yapılır: bir BlockingCollection Içindeki öğeleri kaldırmak Için foreach kullanma](how-to-use-foreach-to-remove.md).
  
## <a name="example"></a>Örnek  
 Bu ilk örnek, koleksiyonun geçici olarak boş (alma sırasında) veya en yüksek kapasiteye (eklenirken) ya da belirtilen bir zaman aşımı süresi geçtiğinde işlemleri engelleyecek şekilde öğelerin nasıl ekleneceğini ve alınacağını gösterir. Maksimum kapasiteden engelleme özelliğinin yalnızca, Oluşturucu içinde belirtilen en fazla kapasite ile BlockingCollection oluşturulduğunda etkinleştirildiğini unutmayın.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Örnek  
 Bu ikinci örnek işlemlerin nasıl ekleneceğini ve öğelerin nasıl alınacağını gösterir. Hiçbir öğe yoksa, sınırlanmış bir koleksiyondaki maksimum kapasiteye ulaşıldı veya zaman aşımı süresi doldu, <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> ya da <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> işlem yanlış döndürür. Bu, iş parçacığının bir süre boyunca başka bir faydalı iş yapmasına ve sonra yeni bir öğe almayı veya daha önce eklenemeyen aynı öğeyi eklemeyi denemesini sağlar. Program ayrıca bir öğesine erişirken iptalin nasıl uygulanacağını gösterir <xref:System.Collections.Concurrent.BlockingCollection%601> .  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [BlockingCollection Genel Bakışı](blockingcollection-overview.md)
