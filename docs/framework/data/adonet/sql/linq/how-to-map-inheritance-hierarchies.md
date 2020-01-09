---
title: 'Nasıl yapılır: devralma hiyerarşilerini eşleme'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 737cb8743d8fd9c93cd46ebf50fba3fe554a35f2
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634670"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Nasıl yapılır: devralma hiyerarşilerini eşleme
LINQ ' de devralma eşlemesini uygulamak için aşağıdaki adımlarda açıklandığı gibi devralma hiyerarşisinin kök sınıfında öznitelikleri ve öznitelik özelliklerini belirtmeniz gerekir. Visual Studio kullanan geliştiriciler, devralma hiyerarşilerini eşlemek için Nesne İlişkisel Tasarımcısı kullanabilir. Bkz. [nasıl yapılır: O/R tasarımcısını kullanarak devralmayı yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
> Alt sınıflarda özel öznitelik veya özellik gerekmez. Özellikle bu alt sınıfların <xref:System.Data.Linq.Mapping.TableAttribute> özniteliğine sahip olmadığına not edin.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Devralma hiyerarşisini eşlemek için  
  
1. Kök sınıfa <xref:System.Data.Linq.Mapping.TableAttribute> özniteliğini ekleyin.  
  
2. Ayrıca, kök sınıfa, hiyerarşi yapısındaki her bir sınıf için bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> özniteliği ekleyin.  
  
3. Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> özniteliği için bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> özelliği tanımlayın.  
  
     Bu özellik, bu veri satırının hangi sınıfa veya alt sınıfa ait olduğunu göstermek için <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> sütunundaki veritabanı tablosunda görünen bir değeri barındırır.  
  
4. Her <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> özniteliği için bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> özelliği de ekleyin.  
  
     Bu özellik, anahtar değerinin hangi sınıf veya alt sınıfa göre olduğunu belirten bir değer içerir.  
  
5. <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> özniteliklerinden yalnızca birinde bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> özelliği ekleyin.  
  
     Bu özellik, veritabanı tablosundan ayrıştırıcı değeri devralma eşlemelerinde herhangi bir <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> değerle eşleşmediği zaman bir *geri dönüş* eşlemesi belirlemek için kullanılır.  
  
6. Bir <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği için <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> özelliği ekleyin.  
  
     Bu özellik, <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> değerini tutan sütun olduğunu belirtir.  
  
## <a name="example"></a>Örnek  
  
> [!NOTE]
> Visual Studio kullanıyorsanız, devralmayı yapılandırmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz. Bkz [. nasıl yapılır: O/R tasarımcısını kullanarak devralmayı yapılandırma](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 Aşağıdaki kod örneğinde, `Vehicle` kök sınıf olarak tanımlanmıştır ve önceki adımlar LINQ hiyerarşisini betimleyen şekilde uygulanmıştır.  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Devralma Desteği](inheritance-support.md)
- [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
