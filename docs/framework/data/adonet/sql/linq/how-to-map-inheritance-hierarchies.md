---
title: "Nasıl yapılır: eşleme devralma hiyerarşileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e9d6215335f6a58de194253cbfe1e539f50d6d84
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-map-inheritance-hierarchies"></a>Nasıl yapılır: eşleme devralma hiyerarşileri
Devralma eşleme uygulamak için [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], öznitelikleri ve öznitelik özellikleri Devralma Hiyerarşisi kök sınıfının aşağıdaki adımlarda açıklandığı gibi belirtmeniz gerekir. Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanabilirsiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] devralma hiyerarşileri eşlemek için. Bkz: [nasıl yapılır: devralma O/R Tasarımcısı kullanarak yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
>  Hiçbir özel öznitelikler veya özellikleri üzerinde alt sınıfların gereklidir. Alt sınıfların olmadığı özellikle Not <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Devralma Hiyerarşisi eşlemek için  
  
1.  Ekleme <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği için kök sınıfı.  
  
2.  Ayrıca kök sınıfına ekleyin bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> her sınıf hiyerarşisi yapısındaki özniteliği.  
  
3.  Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> özniteliği, tanımlayan bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> özelliği.  
  
     Bu özellik veritabanı tablosunda görüntülenen bir değeri tutan <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> hangi sınıfı ya da bir alt kümesi için bu veri satırının ait göstermek için sütun.  
  
4.  Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> özniteliği, ayrıca bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> özelliği.  
  
     Bu özellik, hangi sınıfı ya da bir alt anahtar değeri güveninin belirten bir değeri tutar.  
  
5.  Yalnızca birinde <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> öznitelikleri, ekleme bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> özelliği.  
  
     Belirlemek için bu özelliği hizmet veren bir *geri dönüş* veritabanı tablosunun Ayrıştırıcıyı değerinden herhangi eşleşmediğinde eşleme <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> devralma eşlemeleri değeri.  
  
6.  Ekleme bir <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> özelliği için bir <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.  
  
     Bu özellik bu tutan sütun olduğunu güveninin <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> değeri.  
  
## <a name="example"></a>Örnek  
  
> [!NOTE]
>  Kullanıyorsanız [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] devralma yapılandırmak için. Bkz: [nasıl yapılır: devralma O/R Tasarımcısı kullanarak yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 Aşağıdaki kod örneğinde, `Vehicle` kök sınıf olarak tanımlandığını ve hiyerarşi için açıklamak için önceki adımları uygulanmıştır [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Devralma Desteği](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)  
 [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
