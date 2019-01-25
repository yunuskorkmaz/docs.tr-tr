---
title: Adı &#39; &lt;adı&gt; &#39; bildirilmemiş
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: e52b93980cfc2d162d35b86bd93ce9eeb9875c9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574826"
---
# <a name="name-39ltnamegt39-is-not-declared"></a>Adı &#39; &lt;adı&gt; &#39; bildirilmemiş
Bir deyimi bir programlama öğesine başvuruyor, ancak derleyicinin tam ada sahip bir öğe bulunamıyor.  
  
 **Hata Kimliği:** BC30451  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Başvuran deyiminde adının yazımını kontrol edin. Visual Basic büyük/küçük harfe duyarsızdır, ancak herhangi bir yazım varyasyonu tamamen farklı bir ad kabul edilir. Unutmayın, alt çizgi (`_`) adının bir parçası ve bu nedenle yazım parçası.  
  
2. Üye erişimi işleci olup olmadığını denetleyin (`.`) arasında bir nesne ve onun üye. Örneğin, bir <xref:System.Windows.Forms.TextBox> adlı Denetim `TextBox1`erişmek için kendi <xref:System.Windows.Forms.TextBoxBase.Text%2A> type özelliği `TextBox1.Text`. Bunun yerine, yazarsanız `TextBox1Text`, farklı bir ad oluşturdunuz.  
  
3. Yazım denetimi doğru olduğundan ve herhangi bir nesne üye erişimi sözdizimini doğru ise, öğesi bildirilmiş doğrulayın. Daha fazla bilgi için [bildirilen öğeler](../../programming-guide/language-features/declared-elements/index.md).  
  
4. Programlama öğesine bildirilmişlerse, kapsam içinde olup olmadığını denetleyin. Başvuran deyimi programlama öğesine bildirme bölge dışında ise, öğe adı nitelemeniz gerekebilir. Daha fazla bilgi için [Visual Basic'de kapsam](../../programming-guide/language-features/declared-elements/scope.md).  

5. Tam olarak nitelenmiş tür veya tür ve üye adı kullanmıyorsanız (örneğin, kodunuz bir özellik olarak başvurduğu `MethodInfo.Name` yerine `System.Reflection.MethodInfo.Name`), ekleme bir [Imports deyimi](../statements/imports-statement-net-namespace-and-type.md).

6. SDK stili projeyi derleyin, çalıştığınız (bir proje ile bir \*satırla başlayan .vbproj dosyası `<Project Sdk="Microsoft.NET.Sdk">`) ve bir tür veya üye Microsoft.VisualBasic.dll içinde hata iletisini ifade eder, uygulamanızı yapılandırın Visual Basic çalışma zamanı kitaplığı için bir başvuru ile derleyin. Varsayılan olarak, SDK stilinde projesinde, bir derlemede kitaplığının bir alt katıştırılır.

   Örneğin, aşağıdaki örnekte olduğundan derlenemiyor <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName> yöntemi bulunamıyor. Visual Basic çalışma zamanı, uygulamaya dahil edilen altkümesindeki katıştırılmış değil.  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb)]

   Bu hatayı gidermek için ekleme `<VBRuntime>Default</VBRuntime>` projeleri öğesine `<PropertyGroup>` bölümünde, aşağıdaki gösterildiği gibi Visual Basic proje dosyası.

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>Ayrıca bkz.

- [Bildirimler ve Sabitlere İlişkin Özet](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)
- [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Bildirilen Öğe Adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
