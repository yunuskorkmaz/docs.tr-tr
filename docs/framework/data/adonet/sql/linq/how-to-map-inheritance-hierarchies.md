---
title: 'Nasıl yapılır: Devralma Hiyerarşilerini Eşleme'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 6f437b7f7ae6a414971edb497bc2c84c03674fe8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331838"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Nasıl yapılır: Devralma Hiyerarşilerini Eşleme
Devralma eşlemede uygulamak için [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], öznitelikler ve öznitelik özellikleri devralma hiyerarşisinin kök sınıfında aşağıdaki adımlarda açıklandığı şekilde belirtmeniz gerekir. Visual Studio kullanan geliştiricilerin kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] devralma hiyerarşilerini eşleme için. Bkz: [nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
>  Hiçbir özel öznitelikler veya özellikleri üzerinde alt sınıflarından gerekir. Alt sınıfları olmayan özellikle Not <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Devralma Hiyerarşisi eşlemek için  
  
1. Ekleme <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği için kök sınıfı.  
  
2. Ayrıca kök Sınıf Ekle bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> hiyerarşi yapısı her sınıf için özniteliği.  
  
3. Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> tanımlayın, öznitelik bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> özelliği.  
  
     Bu özellik veritabanı tablosunda görüntülenen bir değeri tutar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> hangi sınıfı veya ImageSource alt sınıfı için bu veri satırının ait belirtmek için sütunu.  
  
4. Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> özniteliği, ayrıca bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> özelliği.  
  
     Bu özellik, hangi sınıfı veya alt anahtar değeri belirtir belirten bir değeri tutar.  
  
5. Yalnızca birinde <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> öznitelikleri, ekleme bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> özelliği.  
  
     Belirlemek için bu özellik hizmet veren bir *geri dönüş* eşleme sırasında veritabanı tablosundan ayrıştırıcı değeri eşleşmiyor <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> devralma eşlemeleri değeri.  
  
6. Ekleme bir <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> özelliği için bir <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.  
  
     Bu özellik bu tutan sütunu olduğunu belirten <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> değeri.  
  
## <a name="example"></a>Örnek  
  
> [!NOTE]
>  Visual Studio kullanıyorsanız, kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] devralmayı yapılandırmak için. Bkz: [nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 Aşağıdaki kod örneğinde, `Vehicle` kök sınıfı tanımlanır ve hiyerarşi için açıklamak için önceki adımları uygulanmıştır [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Devralma Desteği](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)
- [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
