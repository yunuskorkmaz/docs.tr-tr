---
title: "Nasıl yapılır: birincil anahtarlar temsil eder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c832b7c54ecbd1f4c4a3bebcbf7f293b9a45e46c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-represent-primary-keys"></a>Nasıl yapılır: birincil anahtarlar temsil eder
Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> özellikte <xref:System.Data.Linq.Mapping.ColumnAttribute> bir özellik veya alan bir veritabanı sütununa birincil anahtarını temsil eden atamak özniteliği.  
  
 Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Hesaplanan sütunlar birincil anahtarlar olarak desteklemez.  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a>Bir özellik veya alan birincil anahtarı olarak belirtmek için  
  
1.  Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.  
  
2.  Değer olarak belirtin `true`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
