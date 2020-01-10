---
title: "Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan ve Alma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
ms.openlocfilehash: 3f4270d2ec71421bad8974a3e5cd8f1d65db3b74
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711304"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan ve Alma
Bu örnek, hem engelleme hem de engellenmeyen bir şekilde <xref:System.Collections.Concurrent.BlockingCollection%601> öğelerin nasıl ekleneceğini ve kaldırılacağını gösterir. <xref:System.Collections.Concurrent.BlockingCollection%601>hakkında daha fazla bilgi için bkz. [BlockingCollection genel bakış](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
 Boş olana kadar <xref:System.Collections.Concurrent.BlockingCollection%601> nasıl numaralandırılacağı ve daha fazla öğe eklenemeyecek bir örnek için bkz. [nasıl yapılır: bir BlockingCollection Içindeki öğeleri kaldırmak Için foreach kullanma](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).
  
## <a name="example"></a>Örnek  
 Bu ilk örnek, koleksiyonun geçici olarak boş (alma sırasında) veya en yüksek kapasiteye (eklenirken) ya da belirtilen bir zaman aşımı süresi geçtiğinde işlemleri engelleyecek şekilde öğelerin nasıl ekleneceğini ve alınacağını gösterir. Maksimum kapasiteden engelleme özelliğinin yalnızca, Oluşturucu içinde belirtilen en fazla kapasite ile BlockingCollection oluşturulduğunda etkinleştirildiğini unutmayın.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Örnek  
 Bu ikinci örnek işlemlerin nasıl ekleneceğini ve öğelerin nasıl alınacağını gösterir. Hiçbir öğe yoksa, sınırlanmış bir koleksiyondaki maksimum kapasiteye ulaşıldı veya zaman aşımı süresi doldu, <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> veya <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> işlemi false döndürür. Bu, iş parçacığının bir süre boyunca başka bir faydalı iş yapmasına ve sonra yeni bir öğe almayı veya daha önce eklenemeyen aynı öğeyi eklemeyi denemesini sağlar. Program ayrıca bir <xref:System.Collections.Concurrent.BlockingCollection%601>erişirken iptalin nasıl uygulanacağını gösterir.  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [BlockingCollection’a Genel Bakış](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
