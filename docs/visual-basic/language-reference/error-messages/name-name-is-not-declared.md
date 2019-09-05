---
title: "'<name>' adı bildirilmemiş"
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: dfa1d1600c7943e503b4f5ec2e2b8ecd6fbb9fe0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254194"
---
# <a name="name-name-is-not-declared"></a>'\<Name > ' adı bildirilmemiş
Bir ifade bir programlama öğesine başvurur, ancak derleyici bu tam adı taşıyan bir öğe bulamaz.  
  
 **Hata KIMLIĞI:** BC30451  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Başvuran deyimindeki adın yazımını denetleyin. Visual Basic, büyük/küçük harfe duyarlıdır, ancak yazıdaki diğer çeşitçler tamamen farklı bir ad olarak kabul edilir. Alt çizgi (`_`) adının bir parçası olduğunu ve bu nedenle Yazımın bir parçasını unutmayın.  
  
2. Bir nesne ve üyesi arasında üye erişim işlecine (`.`) sahip olup olmadığınızı denetleyin. Örneğin <xref:System.Windows.Forms.TextBox> , adlı `TextBox1`bir denetiminiz varsa, <xref:System.Windows.Forms.TextBoxBase.Text%2A> özelliğine erişmek için yazmanız `TextBox1.Text`gerekir. Bunun yerine `TextBox1Text`, farklı bir ad oluşturdunuz.  
  
3. Yazım doğru ise ve herhangi bir nesne üyesi erişiminin sözdizimi doğru ise, öğenin bildirildiği doğrulayın. Daha fazla bilgi için bkz. [bildirilmiştir öğeleri](../../programming-guide/language-features/declared-elements/index.md).  
  
4. Programlama öğesi bildirilirse, kapsam içinde olup olmadığını kontrol edin. Başvuran ifade, programlama öğesini bildiren bölgenin dışındaysa, öğe adını nitelemeniz gerekebilir. Daha fazla bilgi için [Visual Basic kapsam](../../programming-guide/language-features/declared-elements/scope.md)bölümüne bakın.  

5. Tam nitelikli bir tür veya tür ve üye adı kullanmıyorsanız (örneğin, kodunuz `MethodInfo.Name` `System.Reflection.MethodInfo.Name`yerine bir özelliğe başvurur), bir [içeri aktarmalar ekstresi](../statements/imports-statement-net-namespace-and-type.md)ekleyin.

6. Bir SDK stili proje (satırla \* `<Project Sdk="Microsoft.NET.Sdk">`başlayan bir. vbproj dosyası olan bir proje) derlemeye çalışıyorsanız ve hata iletisi Microsoft. VisualBasic. dll derlemesindeki bir türe veya üyeye başvuruyorsa, uygulamanızı şu şekilde yapılandırın Visual Basic çalışma zamanı kitaplığı başvurusuyla derleyin. Varsayılan olarak, kitaplığın bir alt kümesi, bir SDK stili projesinde derlemeize katıştırılır.

   Örneğin, <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> Yöntem bulunamadığı için aşağıdaki örnek derlenemiyor. Uygulamanıza dahil olan Visual Basic çalışma zamanının alt kümesine Katıştırılamaz.  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   Bu hatayı gidermek için, aşağıdaki Visual Basic `<VBRuntime>Default</VBRuntime>` proje dosyasında gösterildiği gibi `<PropertyGroup>` , öğesini projeler bölümüne ekleyin.

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>Ayrıca bkz.

- [Bildirimler ve Sabitlere İlişkin Özet](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)
- [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Bildirilen Öğe Adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
