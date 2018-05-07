---
title: Öznitelikleri Uygulama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3a0151f6cc3ce25ca0c52a25be328ece8cb4434
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="applying-attributes"></a>Öznitelikleri Uygulama
Kodunuzdaki bir öğeye bir öznitelik uygulamak için aşağıdaki işlemi kullanın.  
  
1.  Ad alanını .NET Framework'ten içe aktararak yeni bir öznitelik tanımlayın veya varolan bir özniteliği kullanın.  
  
2.  Özniteliği öğenin hemen önüne ekleyerek kod öğesine uygulayın.  
  
     Her dilin kendi öznitelik sözdizimi bulunur. C++ ve C#'de öznitelik, köşeli ayraç içine alınır ve öğeden, satır sonu da içerebilen boşluk ile ayrılır. Visual Basic'te öznitelik, açılı ayraç içine alınır ve aynı mantıksal satırda bulunması gerekir; eğer bir satır sonu isterseniz satır devamı karakteri kullanabilirsiniz.
  
3.  Öznitelik için konumsal parametreleri ve adlandırılmış parametreleri belirtin.  
  
     Konumsal parametreler gereklidir ve adlandırılmış parametrelerden önce gelmeleri gerekir; öznitelik oluşturucularından birinin parametrelerine karşılık gelirler. Adlandırılmış parametreler isteğe bağlıdır ve özniteliğin okuma/yazma özelliklerine karşılık gelirler. C++ ve C#, belirtin `name` = `value` her isteğe bağlı bir parametre için burada `name` özelliği adıdır. Visual Basic'te, `name`:=`value` belirtin.  
  
 Kodunuzu derlediğinizde öznitelik meta verilere yayılır ve çalışma zamanı yansıma hizmetleri ile ortak dil çalışma zamanı ve herhangi bir özel araç veya uygulama tarafından kullanılabilir olur.  
  
 Kural gereği, tüm öznitelik adları Öznitelik ile biter. Ancak, Visual Basic ve C# gibi çalışma zamanını hedef alan çeşitli diller, bir özniteliğin tam adını belirtmenizi gerektirmez. Örneğin, başlatmak istiyorsanız <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, yalnızca olarak başvuruda bulunmanız **Kullanımdan kalktı**.  
  
## <a name="applying-an-attribute-to-a-method"></a>Bir Yönteme Öznitelik Uygulama  
 Aşağıdaki kod örneğinde bildirmek gösterilmiştir **System.ObsoleteAttribute**, hangi işaretleri kodu geçersiz. `"Will be removed in next version"` dizesi özniteliğe geçirilir. Bu öznitelik, özniteliğin açıkladığı kod çağırıldığında geçirilen dizeyi görüntüleyen bir derleyici uyarısına neden olur.  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a>Öznitelikleri Derleme Düzeyinde Uygulama  
 Derleme düzeyinde bir öznitelik uygulamak istiyorsanız, kullanmak **derleme** (`Assembly` Visual Basic'te) anahtar sözcüğü. Aşağıdaki kodda gösterildiği **AssemblyTitleAttribute** derleme düzeyinde uygulanır.  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 Bu öznitelik uygulandığında `"My Assembly"` dizesi, dosyanın meta veri bölümündeki derleme bildirimine yerleştirilir. Kullanarak öznitelik görüntüleyebilirsiniz [MSIL ayrıştırıcı (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) veya öznitelik almak üzere özel bir program oluşturarak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öznitelikler](../../../docs/standard/attributes/index.md)  
 [Özniteliklerde Depolanan Bilgileri Alma](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)  
 [Kavramları](/cpp/windows/attributed-programming-concepts)  
 [Öznitelikler](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
