---
title: Veri kümelerini sorgulama (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 79a9b320fbdbfecc3f7d531d992b1529873871a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783043"
---
# <a name="querying-datasets-linq-to-dataset"></a>Veri kümelerini sorgulama (LINQ to DataSet)
Bir <xref:System.Data.DataSet> nesne verilerle doldurulduktan sonra sorgulama işlemine başlayabilirsiniz. Sorguları LINQ to DataSet ile formül, diğer [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]etkin veri kaynaklarında kullanılmasına benzer. Ancak, bir [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] <xref:System.Data.DataSet> nesne üzerinde sorgu kullandığınızda, bir özel türün numaralandırması yerine, <xref:System.Data.DataRow> nesneleri bir numaralandırma sorgulamakta olduğunuz durumlarda unutmayın. Bu, Sorgularınızdaki <xref:System.Data.DataRow> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sınıfının herhangi bir üyesini kullanabileceğiniz anlamına gelir. Bu, zengin, karmaşık sorgular oluşturmanızı sağlar.  
  
 Diğer uygulamalarında [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]olduğu gibi, iki farklı biçimde LINQ to DataSet sorguları oluşturabilirsiniz: sorgu ifadesi sözdizimi ve Yöntem tabanlı sorgu söz dizimi. Sorgu ifadesi söz dizimini veya Yöntem tabanlı sorgu söz dizimini kullanarak <xref:System.Data.DataSet>, bir içindeki birden çok tabloya <xref:System.Data.DataSet>karşı veya bir tür <xref:System.Data.DataSet>içindeki tablolarda tek tek tablolara karşı sorgular gerçekleştirebilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Tek Tablolu Sorgular](single-table-queries-linq-to-dataset.md)  
 Tek tablo sorgularının nasıl gerçekleştirileceğini açıklar.  
  
 [Tablolar Arası Sorgular](cross-table-queries-linq-to-dataset.md)  
 Çapraz tablo sorgularının nasıl gerçekleştirileceğini açıklar.  
  
 [Türü Belirtilmiş DataSet’leri Sorgulama](querying-typed-datasets.md)  
 Yazılan <xref:System.Data.DataSet> nesnelerin nasıl sorgulanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
