---
title: Imports deyimi - .NET Namespace ve türü (Visual Basic)
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
ms.openlocfilehash: 4574bab62ca6d095ab66c17bf186da5f3d79bfb7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826528"
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports Deyimi (.NET Ad Alanı ve Türü)
Etkinleştirir, ad alanı nitelenmeden başvurulmak üzere adlarını yazın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`aliasname`|İsteğe bağlı. Bir *diğer içeri aktarma* veya adı olarak kod başvurabilir `namespace` tam nitelenmiş dize yerine. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Gerekli. İçeri aktarılan ad alanının tam adı. Ad alanları dizisini, herhangi bir düzeyi yuvalanabilir.|  
|`element`|İsteğe bağlı. Bir programlama öğesinin ad alanı bildirimi. Herhangi bir kapsayıcı öğe olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Imports` Deyimi doğrudan başvurulabilmesi için verilen ad alanında bulunan türleri tanır.  
  
 Tek bir ad alanı adı veya iç içe geçmiş ad alanlarının bir dize sağlayabilirsiniz. Her iç içe geçmiş ad alanı sonraki daha yüksek düzey ad alanından noktayla ayrılmış (`.`), aşağıdaki örnekte gösterildiği gibi.  
  
 `Imports System.Collections.Generic`  
  
 Her kaynak dosyası herhangi bir sayıda içerebilir `Imports` deyimleri. Bunlar herhangi bir seçeneği bildirimleri gibi izlemelisiniz `Option Strict` deyimi ve gelmelidir bir programlama öğesi bildirimleri gibi `Module` veya `Class` deyimleri.  
  
 Kullanabileceğiniz `Imports` yalnızca dosya düzeyinde. Bu, içeri aktarma bildirimi bağlamı bir kaynak dosyası olmalıdır ve ad alanı, sınıf, yapı, modül, arabirimi, yordam veya blok olamayacağı anlamına gelir.  
  
 Unutmayın `Imports` deyimi yapmaz öğelerden, diğer projeleri ve derlemeleri projenize kullanılabilir. İçeri aktarma başvuru ayarlama yer almaz. Yalnızca zaten projeniz için kullanılabilir olan adlar nitelemek için ihtiyacını ortadan kaldırır. Daha fazla bilgi için "İçeren öğeleri içeri aktarma" bölümüne bakın. [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
>  Örtük tanımlayabilirsiniz `Imports` deyimleri kullanarak [başvurular sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic). Daha fazla bilgi için [nasıl yapılır: İçeri aktarılan ad alanlarını (Visual Basic) ekleyip](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
## <a name="import-aliases"></a>İçeri aktarma diğer adları  
 Bir *diğer içeri aktarma* diğer adı için bir ad alanı veya tür tanımlar. İçeri aktarma diğer adları, bir veya daha fazla ad alanı içinde bildirilen aynı ada sahip öğeleri kullanmanız gerektiğinde kullanışlıdır. Daha fazla bilgi ve örnek için "Uygun bir öğe adı" bölümüne bakın [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Modül düzeyinde aynı ada sahip bir üye bildirmemelidir `aliasname`. Bunu yaparsanız, Visual Basic Derleyicisi kullanan `aliasname` ve artık yalnızca bildirilen üye için içeri aktarma diğer ad olarak doğrulamalıdır.  
  
 Sonuçları içeri aktarma diğer ad bildirmek için kullanılan sözdizimi gibi bir XML ad alanı öneki almak için kullanılsa da farklıdır. Bir XML ad alanı öneki yalnızca XML sabit değerleri veya XML eksen özellikleri önek bir tam öğe veya öznitelik adı için kullanılabilir ancak içeri aktarma diğer ad, kodunuzda bir ifade olarak kullanılabilir.  
  
### <a name="element-names"></a>Öğe adları  
 Sağlarsanız, `element`, temsil etmelidir bir *kapsayıcı öğe*, diğer bir deyişle, diğer öğeler de içerebilen bir programlama öğesi. Kapsayıcı öğeler, sınıflar, yapılar, modüller, arabirimleri ve sabit listeleri içerir.  
  
 Kapsamı tarafından kullanıma sunulan tüm öğeleri bir `Imports` deyimi bağlı olup olmadığını belirtin üzerinde `element`. Yalnızca belirtirseniz `namespace`, tüm benzersiz adlı söz konusu ad alanının üyeleri ve kapsayıcı öğeleri bu ad alanı içinde üyeleri, nitelenmeden kullanılabilir. Her ikisini de belirtirseniz `namespace` ve `element`, yalnızca o öğenin üyeleri nitelenmeden kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kullanarak C:\ dizindeki tüm klasörleri döndürür <xref:System.IO.DirectoryInfo> sınıfı.  
  
 Kodu olmayan `Imports` deyimini dosyanın üst. Bu nedenle, `DirectoryInfo`, <xref:System.Text.StringBuilder>, ve <xref:Microsoft.VisualBasic.ControlChars.CrLf> başvuruları ad alanları tüm tam olarak nitelenmiş.  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içerir `Imports` deyimleri başvurulan ad alanları için. Bu nedenle, türleri ad alanları tam olarak belirtilmesi gerekmez.  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içerir `Imports` başvurulan ad alanları için diğer adlar oluşturma deyimleri. Tür diğer adları ile nitelenmiştir.  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içerir `Imports` başvurulan tür için diğer adlar oluşturma deyimleri. Diğer adlar türlerini belirtmek için kullanılır.  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Namespace Deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [References ve Imports Deyimi](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports Deyimi (XML Ad Alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
