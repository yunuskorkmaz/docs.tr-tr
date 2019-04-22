---
title: Visual Basic'de Değişkenlerle İlgili Sorun Giderme
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
ms.openlocfilehash: 55d0fdcdbed4f994e50e83e5a25baf83c3ad79cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831130"
---
# <a name="troubleshooting-variables-in-visual-basic"></a>Visual Basic'de Değişkenlerle İlgili Sorun Giderme
Bu sayfada Visual Basic'te değişkenler ile çalışırken oluşabilecek bazı yaygın sorunlar listelenir.  
  
## <a name="unable-to-access-members-of-an-object"></a>Bir nesnenin üyelerine erişmek için  
 Kodunuzu bir özellik veya yöntem bir nesne üzerinde erişmeye çalışırsa, iki olası hata sonuçları vardır:  
  
-   Belirli bir tür olması ve ardından o türe göre tanımlanmamış bir üye başvurmak için nesne değişkenini bildirirseniz, derleyici bir hata iletisi oluşturabilir.  
  
-   Çalışma zamanı <xref:System.MemberAccessException> bir nesne değişkenine atanan nesne kodunuzu erişmeye üye kullanıma sunmuyor oluşur. Bir değişken, söz konusu olduğunda [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md), üyesi değilse bu durum da edinebilirsiniz `Public`. Geç bağlama yalnızca erişime olmasıdır `Public` üyeleri.  
  
 Zaman [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) kümeleri tür denetimini `On`, yalnızca yöntemleri ve özellikleri ile kaydedilebilmeniz bu sınıfın bir nesne değişkenine erişebilir. Aşağıdaki örnek bunu göstermektedir.  

 [!code-vb[VbVbalrVariables#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#2)]  
  
 Bu örnekte, `p` yalnızca üyelerinin kullanabileceği <xref:System.Object> kendisi, hangi içermeyen sınıf `Left` özelliği. Öte yandan, `q` türü olarak bildirildi <xref:System.Windows.Forms.Label>, tüm yöntemleri ve özellikleri kullanabilmesi için <xref:System.Windows.Forms.Label> sınıfını <xref:System.Windows.Forms> ad alanı.  
  
### <a name="correct-approach"></a>Doğru yaklaşımı  
 Bir nesne belirli bir sınıfın tüm üyeleri erişebilmesi için mümkün olduğunda, sınıf türünde olması gereken nesne değişkeni bildirme. Bu, örneğin, derleme zamanında tür nesne bilmiyorsanız işlemi yapamazsınız, ayarlamalısınız `Option Strict` için `Off` ve olmaya değişkenini tanımlamak [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md). Bu nesneleri değişkene atanan herhangi bir tür sağlar ve şu anda atanmış nesneyi kabul edilebilir bir tür olduğundan emin olmak için önlem almalısınız. Kullanabileceğiniz [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md) bunun belirlenmesi için.  
  
## <a name="other-components-cannot-access-your-variable"></a>Diğer bileşenleri Değişkeninizi erişemiyor  
 Visual Basic adları *büyük küçük harf duyarsız*. İki adı yalnızca alfabetik durumda farklıysa, derleyici bunları aynı adı olarak yorumlar. Örneğin, göz önünde bulundurur `ABC` ve `abc` aynı bildirilen öğeye başvurmak üzere.  
  
 Ancak, ortak dil çalışma zamanı (CLR) kullanan *büyük/küçük harfe* bağlama. Bir derleme veya bir DLL üretmek ve diğer derlemeleri kullandırmak, bu nedenle, adları artık büyük küçük harf duyarlıdır. Örneğin, adında bir öğe ile bir sınıf tanımlama `ABC`, ve diğer derlemeler ortak dil çalışma zamanı aracılığıyla sınıfınızın kullanın, öğesine başvurmalıdır `ABC`. Daha sonra sınıfı yeniden derleyin ve öğenin adını değiştirmek `abc`, kendi sınıfınızı kullanarak diğer derlemeler bu öğe artık erişemez. Bu nedenle, bir derleme güncelleştirilmiş bir sürümünü serbest bıraktığınızda, ortak öğeleri alfabetik durumunu değiştirmemesi gerekir.  
  
 Daha fazla bilgi için [ortak dil çalışma zamanı](../../../../standard/clr.md).  
  
### <a name="correct-approach"></a>Doğru yaklaşımı  
 Diğer bileşenleri, değişkenlere erişmek izin vermek için bunlar büyük/küçük harfe değilmiş gibi adlarını kabul eder. Sınıf veya modül test ederken, diğer derlemeler beklediğiniz değişkenlerine bağlama emin olun. Bir bileşen yayımladıktan sonra kullanımları değiştirme dahil olmak üzere var olan değişken adlarının herhangi bir değişiklik yapmayın.  
  
## <a name="wrong-variable-being-used"></a>Yanlış değişken kullanılıyor  
 Aynı ada sahip birden fazla değişken varsa, Visual Basic Derleyicisi her başvuru adı çözümlemeye çalışır. Farklı kapsam değişkenleri varsa, derleyici en dar kapsamdan bildirimiyle başvuru çözümler. Bunlar aynı kapsamda varsa, çözümlemesi başarısız olur ve derleyici bir hata bildirir. Daha fazla bilgi için [bildirilmiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Doğru yaklaşımı  
 Aynı ada ancak farklı kapsam değişkenleri kullanmaktan kaçının. Diğer derlemeleri veya projeleri kullanıyorsanız, bu dış bileşenleri mümkün olduğunca tanımlanan herhangi bir adı kullanarak kaçının. Aynı ada sahip birden fazla değişken varsa, her başvuru uygun emin olun. Daha fazla bilgi için [bildirilmiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Nasıl yapılır: Bir nesnenin üyelerine erişim](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Nasıl yapılır: Bir nesne değişkeninin için hangi türe başvurduğunu belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Bildirilen Öğe Adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
