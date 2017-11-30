---
title: "Imports Deyimi (.NET Ad Alanı ve Türü)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 46cc78c2fd039fb56fd4d1b797f2d09cbe95d317
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imports-statement-net-namespace-and-type"></a>Imports Deyimi (.NET Ad Alanı ve Türü)
Etkinleştirir ad alanı nitelemesiz başvurulacak adlarını yazın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`aliasname`|İsteğe bağlı. Bir *diğer alma* veya adı olarak kod başvurabilir `namespace` yerine tam nitelenmiş dize. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Gerekli. İçeri aktarılan ad alanının tam adı. Ad alanları dizisini herhangi bir düzeye iç içe.|  
|`element`|İsteğe bağlı. Bir programlama öğesi adını ad alanında bildirildi. Herhangi bir kapsayıcı öğe olabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Imports` Deyimi doğrudan başvurulacak belirli bir ad alanında bulunan türleri sağlar.  
  
 Bir tek ad alanı adı veya iç içe geçmiş ad alanları bir dize sağlayabilirsiniz. İç içe geçmiş her ad alanı sonraki yüksek düzey ad alanından virgülle ayrılmış (`.`), aşağıdaki örnekte gösterildiği gibi.  
  
 `Imports System.Collections.Generic`  
  
 Her kaynak dosyasının herhangi bir sayıda içerebilir `Imports` deyimleri. Bu bir seçenek bildirimleri gibi izlemelisiniz `Option Strict` deyimi ve gelmelidir herhangi programlama öğesi bildirimleri gibi `Module` veya `Class` deyimleri.  
  
 Kullanabileceğiniz `Imports` yalnızca dosya düzeyinde. Bu bildirimi bağlam içe aktarılması için bir kaynak dosyası olmalıdır ve ad alanı, sınıf, yapı, modülü, arabirimi, yordamı veya blok olamaz anlamına gelir.  
  
 Unutmayın `Imports` deyimi yapmaz diğer projeler ve derlemeler öğelerinden projeniz için kullanılabilir. İçeri aktarma başvuru ayarlama gerçekleşmez. Yalnızca zaten projeniz için kullanılabilir olan adları nitelemek için gereksinimini ortadan kaldırır. Daha fazla bilgi için bkz: "İçeren öğelerini içe aktarma" [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
>  Örtük tanımlayabilirsiniz `Imports` kullanarak deyimleri [başvurular sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic). Daha fazla bilgi için bkz: [nasıl yapılır: içeri aktarılan ad alanları (Visual Basic) ekleyip](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
## <a name="import-aliases"></a>İçeri aktarma diğer adları  
 Bir *diğer alma* bir ad alanı veya türü için diğer ad tanımlar. İçeri aktarma diğer adları, bir veya daha fazla ad içinde bildirilen aynı ada sahip öğeleri kullanmanız gerektiğinde faydalıdır. Daha fazla bilgi ve bir örnek için "Uygun bir öğe adı" bölümüne bakın [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Modül düzeyinde aynı ada sahip bir üye bildirmelidir değil `aliasname`. Bunu yaparsanız, Visual Basic derleyici kullanan `aliasname` bildirilen üye için yalnızca ve artık alma diğer ad olarak tanır.  
  
 Sonuçları içeri aktarma diğer ad bildirmek için kullanılan sözdizimi gibi bir XML ad alanı öneki içeri aktarmak için kullanılsa da farklıdır. Bir XML ad alanı öneki yalnızca XML değişmez değerleri veya XML eksen özellikleri önek olarak bir tam öğe veya öznitelik adı için kullanılabilir bir içeri aktarma diğer ad, kodunuzda bir ifade olarak kullanılabilir.  
  
### <a name="element-names"></a>Öğe adları  
 Sağladığınız varsa `element`, temsil etmelidir bir *kapsayıcı öğe*, diğer bir deyişle, diğer öğeler içerebilir bir programlama öğesi. Kapsayıcı öğeler, sınıflar, yapılar, modüller, arabirimler ve numaralandırmalar içerir.  
  
 Tarafından kullanılabilir hale öğeleri kapsamını bir `Imports` deyimi bağlı olup olmadığını belirtin üzerinde `element`. Yalnızca belirtirseniz `namespace`, tüm benzersiz adlı bu ad alanı üyeleri ve bu ad alanı içindeki kapsayıcı öğeleri üyeleri, nitelemesiz kullanılabilir. Her ikisini de belirtirseniz, `namespace` ve `element`, yalnızca o öğeye üyeleri nitelemesiz kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kullanarak C:\ dizindeki tüm klasörleri döndürür <xref:System.IO.DirectoryInfo> sınıfı.  
  
 Kod sahip olmayan `Imports` dosyanın en üstüne deyimlerini. Bu nedenle, `DirectoryInfo`, <xref:System.Text.StringBuilder>, ve <xref:Microsoft.VisualBasic.ControlChars.CrLf> başvuruları ad alanları ile tüm tam.  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içerir `Imports` deyimleri başvurulan ad alanları için. Bu nedenle, türleri olan ad alanları tam olması gerekmez.  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içerir `Imports` başvurulan ad alanları için diğer adlar oluşturma deyimleri. Türleri diğer adları ile yetkili olan.  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek içerir `Imports` başvurulan türleri için diğer adlar oluşturma deyimleri. Diğer adlar türlerini belirtmek için kullanılır.  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Namespace deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [References ve Imports deyimi](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [Bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
