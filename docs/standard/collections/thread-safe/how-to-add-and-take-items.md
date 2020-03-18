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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711304"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan ve Alma
Bu örnek, hem engelleme hem <xref:System.Collections.Concurrent.BlockingCollection%601> de engelleme olmayan bir şekilde öğelerin nasıl eklendiğini ve kaldırılmasını gösterir. Daha fazla <xref:System.Collections.Concurrent.BlockingCollection%601>bilgi için, [bkz.](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)  
  
 Boşalana ve başka öğe eklenene kadar a'yı <xref:System.Collections.Concurrent.BlockingCollection%601> nasıl sayısala rendelediğine dair bir örnek için [bkz.](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)
  
## <a name="example"></a>Örnek  
 Bu ilk örnek, koleksiyonun geçici olarak boş alması (alırken) veya maksimum kapasitede (eklerken) veya belirli bir zaman aşımı süresi nin dolması durumunda işlemlerin engellemesi için öğelerin nasıl eklendiğini ve alınacağını gösterir. Maksimum kapasitede engellemenin yalnızca kurucuda belirtilen maksimum kapasiteyle BlockingCollection oluşturulduğunda etkinleştirildiğini unutmayın.  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>Örnek  
 Bu ikinci örnek, işlemlerin engellememesi için öğelerin nasıl eklendiğini ve alınacağını gösterir. Öğe yoksa, sınırlanmış bir koleksiyondaki maksimum kapasiteye ulaşıldı veya zaman aşımı süresi <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> geçti, sonra veya <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> işlem yanlış döndürür. Bu, iş parçacığının bir süre için başka yararlı işler yapmasına ve daha sonra yeni bir öğeyi almak için yeniden denemesine veya daha önce eklenemeyecek aynı öğeyi eklemeye çalışmasına olanak tanır. Program ayrıca bir <xref:System.Collections.Concurrent.BlockingCollection%601>.  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [BlockingCollection Genel Bakışı](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
