---
title: Değişkenlerle İlgili Sorun Giderme
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
ms.openlocfilehash: e2bcf0b779d98ea4b109ea6d33b69a15110d423c
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080172"
---
# <a name="troubleshooting-variables-in-visual-basic"></a>Visual Basic'de Değişkenlerle İlgili Sorun Giderme

Bu sayfada, Visual Basic değişkenlerle çalışırken oluşabilecek bazı yaygın sorunlar listelenmektedir.  
  
## <a name="unable-to-access-members-of-an-object"></a>Bir nesnenin üyelerine erişilemiyor  

 Kodunuz bir nesne üzerindeki bir özelliğe veya yönteme erişmeyi denerse, iki olası hata sonucu vardır:  
  
- Nesne değişkenini belirli bir türde olacak şekilde bildirirseniz derleyici bir hata mesajı oluşturabilir ve ardından bu tür tarafından tanımlanmayan bir üyeye başvurursunuz.  
  
- Bir çalışma zamanı <xref:System.MemberAccessException> , bir nesne değişkenine atanan nesne, kodunuzun erişmeye çalıştığı üyeyi kullanıma sunmadığı zaman oluşur. [Nesne veri türü](../../../language-reference/data-types/object-data-type.md)değişkeni söz konusu olduğunda, üye değilse bu özel durumu da alabilirsiniz `Public` . Bunun nedeni, geç bağlamanın yalnızca üyelere erişim sağlamasına izin verir `Public` .  
  
 [Option Strict deyimin](../../../language-reference/statements/option-strict-statement.md) tür denetimini ayarlaması halinde `On` bir nesne değişkeni, yalnızca onu bildirdiğiniz sınıfın yöntemlerine ve özelliklerine erişebilir. Aşağıdaki örnek bunu göstermektedir.  

 [!code-vb[VbVbalrVariables#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#2)]  
  
 Bu örnekte, `p` yalnızca <xref:System.Object> sınıfının kendisini, özelliğini içermeyen üyelerini kullanabilir `Left` . Diğer taraftan, türü olarak `q` bildirildi <xref:System.Windows.Forms.Label> , bu nedenle <xref:System.Windows.Forms.Label> ad alanındaki sınıfının tüm yöntemlerini ve özelliklerini kullanabilir <xref:System.Windows.Forms> .  
  
### <a name="correct-approach"></a>Doğru yaklaşım  

 Belirli bir sınıfın bir nesnesinin tüm üyelerine erişebilmek için, mümkün olduğunda, nesne değişkenini bu sınıfın türünden olacak şekilde bildirin. Bunu yapmazsanız, örneğin, derleme zamanında nesne türünü bilmediğinizde, `Option Strict` `Off` [nesne veri türü](../../../language-reference/data-types/object-data-type.md)olarak değişkeni olarak ayarlamanız ve belirtmeniz gerekir. Bu, herhangi bir türdeki nesnelerin değişkenine atanmasını sağlar ve şu anda atanmış nesnenin kabul edilebilir bir türde olduğundan emin olmak için gerekli adımları uygulamanız gerekir. Bu belirleme yapmak için [typeof işlecini](../../../language-reference/operators/typeof-operator.md) kullanabilirsiniz.  
  
## <a name="other-components-cannot-access-your-variable"></a>Diğer bileşenler değişkene erişemez  

 Visual Basic adları *büyük/küçük harfe duyarlıdır*. İki ad yalnızca alfabetik durumda farklıysa, derleyici bunları aynı ad olarak yorumlar. Örneğin, `ABC` `abc` aynı tanımlanmış öğeye başvurmak için ve öğesini dikkate alır.  
  
 Ancak, ortak dil çalışma zamanı (CLR) *büyük/küçük harfe duyarlı* bağlama kullanır. Bu nedenle, bir derleme veya DLL oluşturduğunuzda ve diğer derlemeler için kullanılabilir hale getirmek istediğinizde, adlarınız artık büyük/küçük harf duyarsız değildir. Örneğin, adlı bir öğesi olan bir sınıfı tanımlarsanız `ABC` ve diğer derlemeler, ortak dil çalışma zamanı aracılığıyla sınıfınızın kullanımını kullanıyorsa, öğesini olarak öğesine başvurmalıdır `ABC` . Daha sonra sınıfınızı yeniden derlemenize ve öğenin adını olarak değiştirirseniz `abc` , sınıfınızı kullanan diğer derlemeler artık bu öğeye erişemez. Bu nedenle, bir derlemenin güncelleştirilmiş bir sürümünü serbest bırakırsanız, tüm ortak öğelerin alfabetik durumunu değiştirmemelisiniz.  
  
 Daha fazla bilgi için bkz. [ortak dil çalışma zamanı](../../../../standard/clr.md).  
  
### <a name="correct-approach"></a>Doğru yaklaşım  

 Diğer bileşenlerin değişkenlerinizin erişimine izin vermek için adlarını büyük küçük harfe duyarlı gibi değerlendirin. Sınıfınızı veya modülünüzü test ederken, diğer derlemelerin istediğiniz değişkenlere bağladığınızdan emin olun. Bir bileşeni yayımladıktan sonra, durumlarını değiştirme dahil olmak üzere mevcut değişken adlarında herhangi bir değişiklik yapmayın.  
  
## <a name="wrong-variable-being-used"></a>Yanlış değişken kullanılıyor  

 Aynı ada sahip birden fazla değişken varsa Visual Basic derleyici, bu ada yapılan her bir başvuruyu çözümlemeye çalışır. Değişkenlerin kapsamı farklı ise, derleyici en dar kapsama sahip bildirime bir başvuru çözer. Aynı kapsama sahip olmaları durumunda, çözümleme başarısız olur ve derleyici bir hata bildirir. Daha fazla bilgi için bkz. [bildirilmemiş öğelere başvurular](../declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Doğru yaklaşım  

 Aynı ada ancak farklı kapsama sahip değişkenler kullanmaktan kaçının. Diğer derlemeleri veya projeleri kullanıyorsanız, bu dış bileşenlerde tanımlanan adları mümkün olduğunca kullanmaktan kaçının. Aynı ada sahip birden fazla değişken varsa, ona yapılan her başvuruyu nitelediğinizden emin olun. Daha fazla bilgi için bkz. [bildirilmemiş öğelere başvurular](../declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değişkenler](index.md)
- [Değişken Bildirimi](variable-declaration.md)
- [Nesne Değişkenleri](object-variables.md)
- [Nesne Değişken Bildirimi](object-variable-declaration.md)
- [Nasıl yapılır: Bir Nesnenin Üyelerine Erişme](how-to-access-members-of-an-object.md)
- [Nesne Değişkeni Değerleri](object-variable-values.md)
- [Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme](how-to-determine-what-type-an-object-variable-refers-to.md)
- [Bildirilmiş Öğelere Başvurular](../declared-elements/references-to-declared-elements.md)
- [Bildirilen Öğe Adları](../declared-elements/declared-element-names.md)
