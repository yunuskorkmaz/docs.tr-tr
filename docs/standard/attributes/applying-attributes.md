---
title: Öznitelikleri Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET], attributes
- attributes [.NET], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 83cfb1d5b5aa3ebc8651406850a758146fd329d4
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829108"
---
# <a name="apply-attributes"></a>Öznitelikleri uygulama

Kodunuzdaki bir öğeye bir öznitelik uygulamak için aşağıdaki işlemi kullanın.

1. Yeni bir öznitelik tanımlayın veya var olan bir .NET özniteliği kullanın.

2. Özniteliği öğenin hemen önüne ekleyerek kod öğesine uygulayın.

     Her dilin kendi öznitelik sözdizimi bulunur. C++ ve C#'de öznitelik, köşeli ayraç içine alınır ve öğeden, satır sonu da içerebilen boşluk ile ayrılır. Visual Basic'te öznitelik, açılı ayraç içine alınır ve aynı mantıksal satırda bulunması gerekir; eğer bir satır sonu isterseniz satır devamı karakteri kullanabilirsiniz.

3. Öznitelik için konumsal parametreleri ve adlandırılmış parametreleri belirtin.

     *Konumsal* Parametreler gereklidir ve adlandırılmış parametrelerden önce gelmelidir; öznitelik oluşturucularından birinin parametrelerine karşılık gelir. *Adlandırılmış* parametreler isteğe bağlıdır ve özniteliğin okuma/yazma özelliklerine karşılık gelir. C++ ve C# ' de, `name=value` her bir isteğe bağlı parametre için belirtin; burada `name` özelliğin adıdır. Visual Basic ' de, belirtin `name:=value` .

 Kodunuzu derlediğinizde öznitelik meta verilere yayılır ve çalışma zamanı yansıma hizmetleri ile ortak dil çalışma zamanı ve herhangi bir özel araç veya uygulama tarafından kullanılabilir olur.

 Kurala göre, tüm öznitelik adları "Attribute" ile biter. Ancak, Visual Basic ve C# gibi çalışma zamanını hedef alan çeşitli diller, bir özniteliğin tam adını belirtmenizi gerektirmez. Örneğin, başlatmak istiyorsanız <xref:System.ObsoleteAttribute?displayProperty=nameWithType> , yalnızca **eski** olarak başvurulmalıdır.

## <a name="apply-an-attribute-to-a-method"></a>Bir yönteme öznitelik uygulama

 Aşağıdaki kod örneği, kodu eski olarak işaretleyen **System. Kullanımdan kaldırılmış Teattribute**'un nasıl kullanılacağını göstermektedir. `"Will be removed in next version"` dizesi özniteliğe geçirilir. Bu öznitelik, özniteliğin açıkladığı kod çağırıldığında geçirilen dizeyi görüntüleyen bir derleyici uyarısına neden olur.

 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]

## <a name="apply-attributes-at-the-assembly-level"></a>Öznitelikleri derleme düzeyinde Uygula

 Derleme düzeyinde bir öznitelik uygulamak istiyorsanız, `assembly` ( `Assembly` Visual Basic) anahtar sözcüğünü kullanın. Aşağıdaki kod, derleme düzeyinde uygulanan **Assemblytitleözniteliğini** gösterir.

 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]

 Bu öznitelik uygulandığında `"My Assembly"` dizesi, dosyanın meta veri bölümündeki derleme bildirimine yerleştirilir. Özniteliği, [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanarak ya da özniteliği almak için özel bir program oluşturarak görüntüleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelikler](index.md)
- [Özniteliklerde Depolanan Bilgileri Alma](retrieving-information-stored-in-attributes.md)
- [Kavramlar](/cpp/windows/attributed-programming-concepts)
- [Öznitelikler (C#)](../../csharp/programming-guide/concepts/attributes/index.md)
- [Özniteliklere genel bakış (Visual Basic)](../../visual-basic/programming-guide/concepts/attributes/index.md)
