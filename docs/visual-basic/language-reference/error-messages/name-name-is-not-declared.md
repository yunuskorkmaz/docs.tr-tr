---
title: "'<name>' adı bildirilmemiş"
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 76c1ab4fb5f1f8e4c76a06110f4b0f9026cca201
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871541"
---
# <a name="name-name-is-not-declared"></a>'\<name>' adı bildirilmemiş

Bir ifade bir programlama öğesine başvurur, ancak derleyici bu tam adı taşıyan bir öğe bulamaz.  
  
 **Hata kimliği:** BC30451  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Başvuran deyimindeki adın yazımını denetleyin. Visual Basic, büyük/küçük harfe duyarlıdır, ancak yazıdaki diğer çeşitçler tamamen farklı bir ad olarak kabul edilir. Alt çizgi ( `_` ) adının bir parçası olduğunu ve bu nedenle Yazımın bir parçasını unutmayın.  
  
2. Bir nesne ve üyesi arasında üye erişim işlecine () sahip olup olmadığınızı denetleyin `.` . Örneğin, <xref:System.Windows.Forms.TextBox> adlı bir denetiminiz varsa `TextBox1` , özelliğine erişmek için <xref:System.Windows.Forms.TextBoxBase.Text%2A> yazmanız gerekir `TextBox1.Text` . Bunun yerine `TextBox1Text` , farklı bir ad oluşturdunuz.  
  
3. Yazım doğru ise ve herhangi bir nesne üyesi erişiminin sözdizimi doğru ise, öğenin bildirildiği doğrulayın. Daha fazla bilgi için bkz. [bildirilmiştir öğeleri](../../programming-guide/language-features/declared-elements/index.md).  
  
4. Programlama öğesi bildirilirse, kapsam içinde olup olmadığını kontrol edin. Başvuran ifade, programlama öğesini bildiren bölgenin dışındaysa, öğe adını nitelemeniz gerekebilir. Daha fazla bilgi için [Visual Basic kapsam](../../programming-guide/language-features/declared-elements/scope.md)bölümüne bakın.  

5. Tam nitelikli bir tür veya tür ve üye adı kullanmıyorsanız (örneğin, kodunuz yerine bir özelliğe başvurur `MethodInfo.Name` `System.Reflection.MethodInfo.Name` ), bir [içeri aktarmalar ekstresi](../statements/imports-statement-net-namespace-and-type.md)ekleyin.

6. Bir SDK stili proje ( \* satırla başlayan bir. vbproj dosyası olan bir proje) derlemeye çalışıyorsanız `<Project Sdk="Microsoft.NET.Sdk">` ve hata iletisi Microsoft.VisualBasic.dll derlemesinde bir tür veya üyeye başvuruyorsa, uygulamanızı Visual Basic çalışma zamanı kitaplığı başvurusuyla derlemek üzere yapılandırın. Varsayılan olarak, kitaplığın bir alt kümesi, bir SDK stili projesinde derlemeize katıştırılır.

   Örneğin, yöntem bulunamadığı için aşağıdaki örnek derlenemiyor <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> . Uygulamanıza dahil olan Visual Basic çalışma zamanının alt kümesine Katıştırılamaz.  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   Bu hatayı gidermek için, `<VBRuntime>Default</VBRuntime>` `<PropertyGroup>` aşağıdaki Visual Basic proje dosyasında gösterildiği gibi, öğesini projeler bölümüne ekleyin.

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>Ayrıca bkz.

- [Bildirimler ve Sabitlere İlişkin Özet](../keywords/declarations-and-constants-summary.md)
- [Visual Basic Adlandırma Kuralları](../../programming-guide/program-structure/naming-conventions.md)
- [Bildirilen Öğe Adları](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Bildirilmiş Öğelere Başvurular](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
