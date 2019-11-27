---
title: Imports ekstresi-.NET ad alanı ve türü
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: 39fa4e74f973bcb575b5751c387c0b879f4e398d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351076"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports Deyimi (.NET Ad Alanı ve Türü)

Ad alanı nitelendirme olmadan tür adlarına başvurulmalarını sağlar.

## <a name="syntax"></a>Sözdizimi

```vb
Imports [ aliasname = ] namespace
' -or-
Imports [ aliasname = ] namespace.element
```

## <a name="parts"></a>Bölümler

|Terim|Tanım|
|---|---|
|`aliasname`|İsteğe bağlı. Kodun tam nitelendirme dizesi yerine `namespace` başvuruda bulunduğu bir *içeri aktarma diğer* adı veya adı. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`namespace`|Gerekli. İçeri aktarılmakta olan ad alanının tam adı. Herhangi bir düzeye yuvalanmış bir ad alanı dizesi olabilir.|
|`element`|İsteğe bağlı. Ad alanında bildirildiği bir programlama öğesinin adı. Herhangi bir kapsayıcı öğesi olabilir.|

## <a name="remarks"></a>Açıklamalar

`Imports` ifadeye, belirtilen bir ad alanında bulunan türlerin doğrudan başvurmalarını sağlar.

Tek bir ad alanı adı veya iç içe geçmiş ad alanları dizesi sağlayabilirsiniz. Aşağıdaki örnekte gösterildiği gibi, iç içe geçmiş her ad alanı bir nokta (`.`) ile bir sonraki daha yüksek düzey ad alanından ayrılır:

```vb
Imports System.Collections.Generic
```

Her kaynak dosya, herhangi bir sayıda `Imports` deyimi içerebilir. Bunlar, `Option Strict` deyimi gibi herhangi bir seçenek bildirimini izlemelidir ve `Module` veya `Class` deyimleri gibi herhangi bir programlama öğesi bildiriminin önüne gelmelidir.

`Imports` yalnızca dosya düzeyinde kullanabilirsiniz. Bu, içe aktarılması işlemini için bildirim bağlamının bir kaynak dosya olması ve bir ad alanı, sınıf, yapı, modül, arabirim, yordam veya blok olamayacağı anlamına gelir.

`Imports` deyimin, projeniz için kullanılabilir olan diğer projelerden ve derlemelerden öğe olmadığını unutmayın. İçeri aktarma, başvuru ayarlamanın yerini almaz. Yalnızca, projeniz için zaten kullanılabilir olan adları nitelendirme gereksinimini ortadan kaldırır. Daha fazla bilgi için, bkz. "Içerilen öğeleri Içeri aktarma", [belirtilen öğelerin başvuruları](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

> [!NOTE]
> [Başvurular sayfasını, proje tasarımcısını (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)kullanarak örtük `Imports` deyimlerini tanımlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Içeri aktarılan ad alanlarını ekleme veya kaldırma (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).

## <a name="import-aliases"></a>Diğer adları içeri aktar

Bir *içeri aktarma diğer adı* , bir ad alanı veya tür için diğer adı tanımlar. İçeri aktarma diğer adları, bir veya daha fazla ad alanında tanımlanan aynı ada sahip öğeleri kullanmanız gerektiğinde faydalıdır. Daha fazla bilgi ve bir örnek için, bkz. "öğe adını niteleyen", [belirtilen öğelerin başvuruları](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

Modül düzeyinde bir üyeyi, `aliasname`aynı ada sahip olarak bildirmemelisiniz. Bunu yaparsanız, Visual Basic derleyici yalnızca, yalnızca belirtilen üye için `aliasname` kullanır ve bunu artık içeri aktarma diğer adı olarak tanımaz.

Bir içeri aktarma diğer adını bildirmek için kullanılan söz dizimi, bir XML ad alanı önekini içeri aktarmak için kullanılan gibidir, ancak sonuçlar farklı olur. Bir içeri aktarma diğer adı kodunuzda bir ifade olarak kullanılabilir, ancak bir XML ad alanı ön eki yalnızca XML sabit değerlerinde veya XML eksen özelliklerinde nitelenmiş bir öğe veya öznitelik adı ön eki olarak kullanılabilir.

### <a name="element-names"></a>Öğe adları

`element`sağlarsanız, bir *kapsayıcı öğe*, diğer bir deyişle diğer öğeleri içerebilen bir programlama öğesi temsil etmelidir. Kapsayıcı öğeleri sınıflar, yapılar, modüller, arabirimler ve numaralandırmalar içerir.

Bir `Imports` deyimin kullanımına sunulan öğelerin kapsamı, `element`belirtdiğinize bağlıdır. Yalnızca `namespace`belirtirseniz, bu ad alanı için benzersiz olarak adlandırılan tüm Üyeler ve bu ad alanı içindeki kapsayıcı öğelerinin üyeleri, nitelendirme olmadan kullanılabilir. Hem `namespace` hem de `element`belirtirseniz, yalnızca bu öğenin üyeleri nitelendirme olmadan kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.IO.DirectoryInfo> sınıfını kullanarak *C:\\* dizinindeki tüm klasörleri döndürür:

Kodun, dosyanın üst kısmında `Imports` deyimleri yok. Bu nedenle, <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>ve <xref:Microsoft.VisualBasic.ControlChars.CrLf> başvuruları ad alanlarıyla tamamen nitelenir.

[!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, başvurulan ad alanları için `Imports` deyimlerini içerir. Bu nedenle, türlerin ad alanları ile tam nitelikli olması gerekmez.

[!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]

[!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, başvurulan ad alanları için diğer adlar oluşturan `Imports` deyimlerini içerir. Türler diğer adlarla nitelenir.

[!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]

[!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, başvurulan türler için diğer adlar oluşturan `Imports` deyimlerini içerir. Diğer adlar, türleri belirtmek için kullanılır.

[!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]

[!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Namespace Deyimi](namespace-statement.md)
- [Visual Basic ad alanları](../../programming-guide/program-structure/namespaces.md)
- [References ve Imports Deyimi](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports Deyimi (XML Ad Alanı)](imports-statement-xml-namespace.md)
- [Bildirilmiş Öğelere Başvurular](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
