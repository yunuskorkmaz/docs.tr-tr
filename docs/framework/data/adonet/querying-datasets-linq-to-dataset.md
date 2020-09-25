---
title: Veri kümelerini sorgulama (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: f42cd792772a4e2b9f24ea8f76ea588da10d9c51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184982"
---
# <a name="querying-datasets-linq-to-dataset"></a>Veri kümelerini sorgulama (LINQ to DataSet)

Bir <xref:System.Data.DataSet> nesne verilerle doldurulduktan sonra sorgulama işlemine başlayabilirsiniz. Sorguları LINQ to DataSet ile formül, diğer LINQ özellikli veri kaynaklarına karşı dil ile tümleşik sorgu (LINQ) kullanılmasına benzer. Ancak, bir nesne üzerinde LINQ sorguları kullandığınızda <xref:System.Data.DataSet> , bir <xref:System.Data.DataRow> özel türün numaralandırması yerine nesnelerin bir listesini sorgulamakta olduğunuzu unutmayın. Bu, LINQ Sorgularınızdaki sınıfının herhangi bir üyesini kullanabileceğiniz anlamına gelir <xref:System.Data.DataRow> . Bu, zengin, karmaşık sorgular oluşturmanızı sağlar.  
  
 Diğer LINQ uygulamalarında olduğu gibi, iki farklı biçimde LINQ to DataSet sorguları oluşturabilirsiniz: sorgu ifadesi sözdizimi ve Yöntem tabanlı sorgu söz dizimi. Sorgu ifadesi söz dizimini veya Yöntem tabanlı sorgu söz dizimini kullanarak, bir içindeki <xref:System.Data.DataSet> birden çok tabloya karşı <xref:System.Data.DataSet> veya bir tür içindeki tablolarda tek tek tablolara karşı sorgular gerçekleştirebilirsiniz <xref:System.Data.DataSet> .  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Tek Tablolu Sorgular](single-table-queries-linq-to-dataset.md)  
 Tek tablo sorgularının nasıl gerçekleştirileceğini açıklar.  
  
 [Tablolar Arası Sorgular](cross-table-queries-linq-to-dataset.md)  
 Çapraz tablo sorgularının nasıl gerçekleştirileceğini açıklar.  
  
 [Türü Belirtilmiş DataSet’leri Sorgulama](querying-typed-datasets.md)  
 Yazılan nesnelerin nasıl sorgulanılacağını açıklar <xref:System.Data.DataSet> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
