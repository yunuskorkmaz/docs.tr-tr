---
title: Visual Basic'de Değişkenlerle İlgili Sorun Giderme
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6b14b3f48dbe9e74879d232966a07fa29bb1102c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshooting-variables-in-visual-basic"></a>Visual Basic'de Değişkenlerle İlgili Sorun Giderme
Bu sayfada Visual Basic'de değişkenlerle birlikte çalışırken ortaya çıkabilecek bazı yaygın sorunlar listelenir.  
  
## <a name="unable-to-access-members-of-an-object"></a>Bir nesnenin üyelerine erişim oluşturulamıyor  
 Kodunuzu bir özellik veya yöntem bir nesne üzerinde erişmeye çalışırsa, iki olası hata sonuçları vardır:  
  
-   Belirli bir türde olması ve bu türüne göre tanımlanmamış bir üyesine başvurmak için nesne değişkeni bildirirseniz derleyici bir hata iletisi oluşturabilir.  
  
-   Çalışma zamanında <xref:System.MemberAccessException> bir nesne değişkenine atanan nesne kodunuzu erişmeye üye göstermiyor oluşur. Bir değişken durumunda [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md), üyesi değilse, bu özel durum da alabilirsiniz `Public`. Geç bağlama yalnızca erişime olmasıdır `Public` üyeleri.  
  
 Zaman [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) kümeleri tür denetimini gerçekleştireceğini `On`, bir nesne değişkeninin yalnızca yöntemleri ve hangi bildirdiğiniz onu sınıfının özelliklerine erişebilir. Aşağıdaki örnek bunu göstermektedir.  

 [!code-vb[VbVbalrVariables#2](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]  
  
 Bu örnekte, `p` yalnızca üyeleri kullanabilirsiniz <xref:System.Object> sınıfının kendisini, hangi içermeyen `Left` özelliği. Diğer taraftan, `q` türünde olması bildirildi <xref:System.Windows.Forms.Label>, tüm yöntemleri ve özellikleri kullanabilmesi için <xref:System.Windows.Forms.Label> sınıfını <xref:System.Windows.Forms> ad alanı.  
  
### <a name="correct-approach"></a>Doğru yaklaşımı  
 Bir nesne belirli bir sınıfın tüm üyelerini erişebilmeleri için mümkün olduğunda, bu sınıfın türüne sahip olması gereken nesne değişkeni bildirme. Bu, derleme zamanında yazın nesne bilmiyorsanız, örneğin yapamayacağı, ayarlamalısınız `Option Strict` için `Off` ve olmaya değişkeni bildirme [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md). Bu nesneleri değişkenine atanan herhangi bir türde sağlar ve şu anda atanmış nesne kabul edilebilir bir türde olduğundan emin olmak için önlem almanız gerekir. Kullanabileceğiniz [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md) bunun belirlenmesi için.  
  
## <a name="other-components-cannot-access-your-variable"></a>Diğer bileşenler değişkeniniz erişemiyor  
 Visual Basic adları *büyük küçük harf duyarsız*. İki adı yalnızca alfabetik durumda farklıysa, derleyicinin bunları aynı adı taşıyan yorumlar. Örneğin, göz önünde bulundurur `ABC` ve `abc` aynı bildirilen öğe başvurmak için.  
  
 Ancak, ortak dil çalışma zamanı (CLR) kullanan *büyük küçük harfe duyarlı* bağlama. Bir derlemeyi ya da bir DLL oluşturabilir ve diğer derlemeler için kullanılabilir hale getirmek, bu nedenle, adlarınızı artık büyük küçük harfe duyarsızdır. Örneğin, bir sınıf olarak adlandırılan bir öğesiyle tanımlarsanız `ABC`, ve diğer derlemelerden ortak dil çalışma zamanı sınıfınızın kullanın, öğesine başvurmalıdır `ABC`. Daha sonra sınıfınız derlenir ve öğenin adını değiştirmek, `abc`, sınıfınız kullanarak diğer derlemeler bu öğe artık erişemez. Bu nedenle, bir derlemeyi güncelleştirilmiş bir sürümünü serbest bıraktığınızda, herhangi bir genel öğesi alfabetik durumunda değiştirmemelisiniz.  
  
 Daha fazla bilgi için bkz: [ortak dil çalışma zamanı](../../../../standard/clr.md).  
  
### <a name="correct-approach"></a>Doğru yaklaşımı  
 Değişkenlerinizi erişmek diğer bileşenleri izin vermek için büyük küçük harfe duyarlı sanki adlarını kabul eder. Sınıf veya modülü sınarken diğer derlemelerden beklediğiniz değişkenlerine bağlama emin olun. Bir bileşenin yayımladıktan sonra çalışmalarına değiştirme gibi varolan değişken adları için herhangi bir değişiklik yapmayın.  
  
## <a name="wrong-variable-being-used"></a>Kullanılan yanlış değişkeni  
 Aynı ada sahip birden fazla değişken varsa, Visual Basic derleyici her başvuru adı çözümlemeye çalışır. Değişkenleri farklı bir kapsam varsa, derleyici dar kapsamı bildirimiyle başvuru çözümler. Bunlar aynı kapsamı varsa, çözümleme başarısız olur ve derleyici bir hata bildirir. Daha fazla bilgi için bkz: [bildirilmiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Doğru yaklaşımı  
 Aynı adlı ancak farklı bir kapsam değişkenleri kullanmaktan kaçının. Diğer derlemeleri veya projeleri kullanıyorsanız, bu dış bileşenlerinde mümkün olduğunca tanımlanan adlar kullanmaktan kaçının. Aynı ada sahip birden fazla değişken varsa, her referansı nitelemek emin olun. Daha fazla bilgi için bkz: [bildirilmiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Nesne Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Nasıl yapılır: Bir Nesnenin Üyelerine Erişme](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Bildirilen Öğe Adları](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
