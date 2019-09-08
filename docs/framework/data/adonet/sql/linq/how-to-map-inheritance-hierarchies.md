---
title: 'Nasıl yapılır: Devralma Hiyerarşilerini Eşleme'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1366e8f5f79a8e695e52c405e20a894861453ae7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781774"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Nasıl yapılır: Devralma Hiyerarşilerini Eşleme
' De [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]devralma eşlemesini uygulamak için aşağıdaki adımlarda açıklandığı gibi devralma hiyerarşisinin kök sınıfında öznitelikleri ve öznitelik özelliklerini belirtmeniz gerekir. Visual Studio kullanan geliştiriciler, devralma hiyerarşilerini eşlemek için Nesne İlişkisel Tasarımcısı kullanabilir. Bkz [. nasıl yapılır: O/R tasarımcısını](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)kullanarak devralmayı yapılandırın.  
  
> [!NOTE]
> Alt sınıflarda özel öznitelik veya özellik gerekmez. Özellikle bu alt sınıfların <xref:System.Data.Linq.Mapping.TableAttribute> özniteliğe sahip olmadığına not edin.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Devralma hiyerarşisini eşlemek için  
  
1. <xref:System.Data.Linq.Mapping.TableAttribute> Özniteliği kök sınıfa ekleyin.  
  
2. Ayrıca, kök sınıfa, hiyerarşi yapısındaki her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> bir sınıf için bir öznitelik ekleyin.  
  
3. Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> öznitelik için bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> Özellik tanımlayın.  
  
     Bu özellik, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> bu veri satırının hangi sınıfa veya alt sınıfa ait olduğunu göstermek için sütunundaki veritabanı tablosunda görünen bir değeri barındırır.  
  
4. Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> öznitelik için de bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> özellik ekleyin.  
  
     Bu özellik, anahtar değerinin hangi sınıf veya alt sınıfa göre olduğunu belirten bir değer içerir.  
  
5. <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> Özniteliklerden yalnızca birinde bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> özellik ekleyin.  
  
     Bu özellik, veritabanı tablosundan ayrıştırıcı değeri devralma eşlemelerinde hiçbir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> değerle eşleşmediği zaman bir *geri dönüş* eşlemesi belirlemek için kullanılır.  
  
6. Öznitelik için bir <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> özellik ekleyin. <xref:System.Data.Linq.Mapping.ColumnAttribute>  
  
     Bu özellik, bu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> değeri tutan sütun olduğunu belirtir.  
  
## <a name="example"></a>Örnek  
  
> [!NOTE]
> Visual Studio kullanıyorsanız, devralmayı yapılandırmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz. Bkz [. nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 Aşağıdaki kod örneğinde, `Vehicle` kök sınıf olarak tanımlanmıştır ve önceki adımlar için [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]hiyerarşiyi betimleyen şekilde uygulanmıştır.  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Devralma Desteği](inheritance-support.md)
- [Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
