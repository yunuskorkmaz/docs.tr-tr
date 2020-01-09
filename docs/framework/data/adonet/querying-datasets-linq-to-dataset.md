---
title: Veri kümelerini sorgulama (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: bb64abcffdbbcd46dfb11b2564619c565e461436
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634787"
---
# <a name="querying-datasets-linq-to-dataset"></a>Veri kümelerini sorgulama (LINQ to DataSet)
<xref:System.Data.DataSet> nesne verilerle doldurulduktan sonra, sorgulama işlemine başlayabilirsiniz. Sorguları LINQ to DataSet ile formül, diğer LINQ özellikli veri kaynaklarına karşı dil ile tümleşik sorgu (LINQ) kullanılmasına benzer. Ancak, <xref:System.Data.DataSet> nesnesi üzerinde LINQ sorguları kullandığınızda, özel bir türün numaralandırılması yerine <xref:System.Data.DataRow> nesnelerinin bir listesini sorgulamakta olduğunuzu unutmayın. Bu, LINQ sorgularınızda <xref:System.Data.DataRow> sınıfının herhangi bir üyesini kullanabileceğiniz anlamına gelir. Bu, zengin, karmaşık sorgular oluşturmanızı sağlar.  
  
 Diğer LINQ uygulamalarında olduğu gibi, iki farklı biçimde LINQ to DataSet sorguları oluşturabilirsiniz: sorgu ifadesi sözdizimi ve Yöntem tabanlı sorgu söz dizimi. Sorgu ifadesi söz dizimini veya Yöntem tabanlı sorgu söz dizimini kullanarak bir <xref:System.Data.DataSet>tek tablolara karşı sorgular gerçekleştirebilir, bir <xref:System.Data.DataSet>birden çok tabloya karşı veya yazılan <xref:System.Data.DataSet>tablolardaki tablolara karşı sorgu sözdizimini kullanabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Tek Tablolu Sorgular](single-table-queries-linq-to-dataset.md)  
 Tek tablo sorgularının nasıl gerçekleştirileceğini açıklar.  
  
 [Tablolar Arası Sorgular](cross-table-queries-linq-to-dataset.md)  
 Çapraz tablo sorgularının nasıl gerçekleştirileceğini açıklar.  
  
 [Türü Belirtilmiş DataSet’leri Sorgulama](querying-typed-datasets.md)  
 Yazılan <xref:System.Data.DataSet> nesnelerinin nasıl sorgulanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
