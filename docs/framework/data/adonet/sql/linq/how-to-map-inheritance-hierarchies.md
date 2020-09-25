---
title: 'Nasıl yapılır: Devralma Hiyerarşilerini Eşleme'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: c0709fde96a5d2f39f04a08ccd24ddf90c782f30
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166423"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Nasıl yapılır: Devralma Hiyerarşilerini Eşleme

LINQ ' de devralma eşlemesini uygulamak için aşağıdaki adımlarda açıklandığı gibi devralma hiyerarşisinin kök sınıfında öznitelikleri ve öznitelik özelliklerini belirtmeniz gerekir. Visual Studio kullanan geliştiriciler, devralma hiyerarşilerini eşlemek için Nesne İlişkisel Tasarımcısı kullanabilir. Bkz. [nasıl yapılır: O/R tasarımcısını kullanarak devralmayı yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
> Alt sınıflarda özel öznitelik veya özellik gerekmez. Özellikle bu alt sınıfların özniteliğe sahip olmadığına not edin <xref:System.Data.Linq.Mapping.TableAttribute> .  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Devralma hiyerarşisini eşlemek için  
  
1. <xref:System.Data.Linq.Mapping.TableAttribute>Özniteliği kök sınıfa ekleyin.  
  
2. Ayrıca, kök sınıfa, <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> hiyerarşi yapısındaki her bir sınıf için bir öznitelik ekleyin.  
  
3. Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> öznitelik için bir özellik tanımlayın <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> .  
  
     Bu özellik, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> Bu veri satırının hangi sınıfa veya alt sınıfa ait olduğunu göstermek için sütunundaki veritabanı tablosunda görünen bir değeri barındırır.  
  
4. Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> öznitelik için de bir özellik ekleyin <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> .  
  
     Bu özellik, anahtar değerinin hangi sınıf veya alt sınıfa göre olduğunu belirten bir değer içerir.  
  
5. Özniteliklerden yalnızca birinde <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> özellik ekleyin.  
  
     Bu özellik, veritabanı tablosundan ayrıştırıcı değeri devralma eşlemelerinde hiçbir değerle eşleşmediği zaman bir *geri dönüş* eşlemesi belirlemek için kullanılır <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> .  
  
6. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>Öznitelik için bir özellik ekleyin <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
     Bu özellik, bu değeri tutan sütun olduğunu belirtir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> .  
  
## <a name="example"></a>Örnek  
  
> [!NOTE]
> Visual Studio kullanıyorsanız, devralmayı yapılandırmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz. Bkz [. nasıl yapılır: O/R tasarımcısını kullanarak devralmayı yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 Aşağıdaki kod örneğinde, `Vehicle` kök sınıf olarak tanımlanmıştır ve önceki adımlar LINQ hiyerarşisini betimleyen şekilde uygulanmıştır.  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Devralma Desteği](inheritance-support.md)
- [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
