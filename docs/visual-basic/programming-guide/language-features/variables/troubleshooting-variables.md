---
title: Değişkenlerle İlgili Sorun Giderme
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
ms.openlocfilehash: 929540788e8134760446e02c3377e78d00ca17d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351767"
---
# <a name="troubleshooting-variables-in-visual-basic"></a>Visual Basic'de Değişkenlerle İlgili Sorun Giderme
Bu sayfada, Visual Basic değişkenlerle çalışırken oluşabilecek bazı yaygın sorunlar listelenmektedir.  
  
## <a name="unable-to-access-members-of-an-object"></a>Bir nesnenin üyelerine erişilemiyor  
 Kodunuz bir nesne üzerindeki bir özelliğe veya yönteme erişmeyi denerse, iki olası hata sonucu vardır:  
  
- Nesne değişkenini belirli bir türde olacak şekilde bildirirseniz derleyici bir hata mesajı oluşturabilir ve ardından bu tür tarafından tanımlanmayan bir üyeye başvurursunuz.  
  
- Bir çalışma zamanı <xref:System.MemberAccessException>, bir nesne değişkenine atanan nesne, kodunuzun erişmeye çalıştığı üyeyi kullanıma sunmadığı zaman oluşur. [Nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)değişkeni söz konusu olduğunda, üye `Public`değilse bu özel durumu da alabilirsiniz. Bunun nedeni, geç bağlamanın yalnızca `Public` üyelerine erişim sağlamasına izin verir.  
  
 [Option Strict deyimin](../../../../visual-basic/language-reference/statements/option-strict-statement.md) türü denetim `On`ayarlarsa, bir nesne değişkeni yalnızca bunu bildirdiğiniz sınıfın yöntemlerine ve özelliklerine erişebilir. Aşağıdaki örnek bunu göstermektedir.  

 [!code-vb[VbVbalrVariables#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#2)]  
  
 Bu örnekte `p`, yalnızca <xref:System.Object> sınıfının kendisini `Left` özelliğini içermeyen üyeleri kullanabilir. Diğer taraftan, `q` <xref:System.Windows.Forms.Label>türünde olduğu bildirildi, bu nedenle <xref:System.Windows.Forms> ad alanındaki <xref:System.Windows.Forms.Label> sınıfının tüm yöntemlerini ve özelliklerini kullanabilir.  
  
### <a name="correct-approach"></a>Doğru yaklaşım  
 Belirli bir sınıfın bir nesnesinin tüm üyelerine erişebilmek için, mümkün olduğunda, nesne değişkenini bu sınıfın türünden olacak şekilde bildirin. Bunu yapamediğinizde, örneğin, derleme zamanında nesne türünü görmüyorsanız, `Off` `Option Strict` ayarlamanız ve değişkeni [nesne veri türünde](../../../../visual-basic/language-reference/data-types/object-data-type.md)olacak şekilde bildirmeniz gerekir. Bu, herhangi bir türdeki nesnelerin değişkenine atanmasını sağlar ve şu anda atanmış nesnenin kabul edilebilir bir türde olduğundan emin olmak için gerekli adımları uygulamanız gerekir. Bu belirleme yapmak için [typeof işlecini](../../../../visual-basic/language-reference/operators/typeof-operator.md) kullanabilirsiniz.  
  
## <a name="other-components-cannot-access-your-variable"></a>Diğer bileşenler değişkene erişemez  
 Visual Basic adları *büyük/küçük harfe duyarlıdır*. İki ad yalnızca alfabetik durumda farklıysa, derleyici bunları aynı ad olarak yorumlar. Örneğin, `ABC` ve `abc` aynı tanımlanmış öğeye başvuracak şekilde değerlendirir.  
  
 Ancak, ortak dil çalışma zamanı (CLR) *büyük/küçük harfe duyarlı* bağlama kullanır. Bu nedenle, bir derleme veya DLL oluşturduğunuzda ve diğer derlemeler için kullanılabilir hale getirmek istediğinizde, adlarınız artık büyük/küçük harf duyarsız değildir. Örneğin, `ABC`adlı bir öğe içeren bir sınıf tanımlarsanız ve diğer derlemeler, ortak dil çalışma zamanı aracılığıyla sınıfınızın kullanımını kullanıyorsa, öğe `ABC`olarak başvurmalıdır. Daha sonra sınıfınızı yeniden derleyerek ve öğenin adını `abc`değiştirirseniz, sınıfınızı kullanan diğer derlemeler artık bu öğeye erişemez. Bu nedenle, bir derlemenin güncelleştirilmiş bir sürümünü serbest bırakırsanız, tüm ortak öğelerin alfabetik durumunu değiştirmemelisiniz.  
  
 Daha fazla bilgi için bkz. [ortak dil çalışma zamanı](../../../../standard/clr.md).  
  
### <a name="correct-approach"></a>Doğru yaklaşım  
 Diğer bileşenlerin değişkenlerinizin erişimine izin vermek için adlarını büyük küçük harfe duyarlı gibi değerlendirin. Sınıfınızı veya modülünüzü test ederken, diğer derlemelerin istediğiniz değişkenlere bağladığınızdan emin olun. Bir bileşeni yayımladıktan sonra, durumlarını değiştirme dahil olmak üzere mevcut değişken adlarında herhangi bir değişiklik yapmayın.  
  
## <a name="wrong-variable-being-used"></a>Yanlış değişken kullanılıyor  
 Aynı ada sahip birden fazla değişken varsa Visual Basic derleyici, bu ada yapılan her bir başvuruyu çözümlemeye çalışır. Değişkenlerin kapsamı farklı ise, derleyici en dar kapsama sahip bildirime bir başvuru çözer. Aynı kapsama sahip olmaları durumunda, çözümleme başarısız olur ve derleyici bir hata bildirir. Daha fazla bilgi için bkz. [bildirilmemiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Doğru yaklaşım  
 Aynı ada ancak farklı kapsama sahip değişkenler kullanmaktan kaçının. Diğer derlemeleri veya projeleri kullanıyorsanız, bu dış bileşenlerde tanımlanan adları mümkün olduğunca kullanmaktan kaçının. Aynı ada sahip birden fazla değişken varsa, ona yapılan her başvuruyu nitelediğinizden emin olun. Daha fazla bilgi için bkz. [bildirilmemiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Nasıl yapılır: Bir Nesnenin Üyelerine Erişme](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Bildirilen Öğe Adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
