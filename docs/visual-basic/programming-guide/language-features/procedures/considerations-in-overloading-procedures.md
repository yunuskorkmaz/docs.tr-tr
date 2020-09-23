---
title: Yordamları Aşırı Yüklemeye İlişkin Düşünceler
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: 6197fa4041a22944542b2657e35bc293a6e5c244
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075063"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>Yordamları Aşırı Yüklemeye İlişkin Düşünceler (Visual Basic)

Bir yordamı aşırı yüklerken, her aşırı yüklenmiş sürüm için farklı bir *imza* kullanmanız gerekir. Bu genellikle her sürümün farklı bir parametre listesi belirtmesi gerektiği anlamına gelir. Daha fazla bilgi için [yordam aşırı](./procedure-overloading.md)yüklemesinde "farklı imza" başlığına bakın.  
  
 Yordamı `Function` `Sub` farklı imzaya sahip olmaları kaydıyla, prosedürü bir yordam ile aşırı yükleyebilirsiniz. İki aşırı yükleme yalnızca, bir dönüş değerine sahip ve diğeri değil ' de farklı olamaz.  
  
 Bir özelliği, bir yordamı aşırı yükle aynı şekilde ve aynı kısıtlamalara sahip olacak şekilde aşırı yükleyebilirsiniz. Ancak, bir yordamı özellik ile aşırı yükleyemez veya tam tersi de geçerlidir.  
  
## <a name="alternatives-to-overloaded-versions"></a>Aşırı yüklenmiş sürümlerin alternatifleri  

 Bazen, özellikle bağımsız değişkenlerin varlığı isteğe bağlı olduğunda veya bu sayının değişken olduğu durumlarda aşırı yüklenmiş sürümlerin alternatifleri vardır.  
  
 İsteğe bağlı bağımsız değişkenlerin tüm diller tarafından desteklenmeyeceğini ve parametre dizilerinin Visual Basic sınırlı olduğunu aklınızda bulundurun. Birçok farklı dilde yazılmış koddan çağrılabilir olabilecek bir yordam yazıyorsanız, aşırı yüklenmiş sürümler en büyük esnekliği sunar.  
  
### <a name="overloads-and-optional-arguments"></a>Aşırı yüklemeler ve Isteğe bağlı bağımsız değişkenler  

 Çağıran kod isteğe bağlı olarak bir veya daha fazla bağımsız değişken sağlayabilir ya da atlayabilir, birden fazla aşırı yüklü sürümü tanımlayabilir veya isteğe bağlı parametreleri kullanabilirsiniz.  
  
#### <a name="when-to-use-overloaded-versions"></a>Aşırı yüklenmiş sürümlerin ne zaman kullanılacağı  

 Aşağıdaki durumlarda aşırı yüklenmiş bir dizi sürümü tanımlamayı düşünebilirsiniz:  
  
- Yordam kodundaki mantık, çağıran kodun isteğe bağlı bir bağımsız değişken olmasına bağlı olarak önemli ölçüde farklılık gösteriyor.  
  
- Yordam kodu, çağıran kodun isteğe bağlı bir bağımsız değişken sağlayıp sağlamadığını güvenilir bir şekilde test edemez. Bu durum, örneğin, çağıran kodun sağlaması beklenmediği bir varsayılan değer için olası bir aday yoksa olur.  
  
#### <a name="when-to-use-optional-parameters"></a>Isteğe bağlı parametrelerin ne zaman kullanılacağı  

 Aşağıdaki durumlarda bir veya daha fazla isteğe bağlı parametre tercih edebilirsiniz:  
  
- Çağıran kod için isteğe bağlı bir bağımsız değişken sağlamadan yalnızca gerekli olan eylem, parametreyi varsayılan bir değere ayarlayamamalıdır. Böyle bir durumda, bir veya daha fazla parametre içeren tek bir sürüm tanımlarsanız yordam kodu daha karmaşık olabilir `Optional` .  
  
 Daha fazla bilgi için bkz. [Isteğe bağlı parametreler](./optional-parameters.md).  
  
### <a name="overloads-and-paramarrays"></a>Aşırı yüklemeler ve ParamArrays  

 Çağıran kod, değişken sayıda bağımsız değişken geçebilirler, birden fazla aşırı yüklenmiş sürüm tanımlayabilir veya bir parametre dizisi kullanabilirsiniz.  
  
#### <a name="when-to-use-overloaded-versions"></a>Aşırı yüklenmiş sürümlerin ne zaman kullanılacağı  

 Aşağıdaki durumlarda aşırı yüklenmiş bir dizi sürümü tanımlamayı düşünebilirsiniz:  
  
- Çağıran kodun parametre dizisine çok az sayıda değerden fazlasını geçirmediğini bilirsiniz.  
  
- Yordam kodundaki mantık, çağıran kodun kaç değere geçirdiğine bağlı olarak önemli ölçüde farklılık gösteriyor.  
  
- Çağıran kod, farklı veri türlerinin değerlerini geçirebilir.  
  
#### <a name="when-to-use-a-parameter-array"></a>Parametre dizisi ne zaman kullanılır?  

 Aşağıdaki durumlarda bir parametre tarafından daha iyi hizmet verilmiştir `ParamArray` :  
  
- Çağıran kodun parametre dizisine kaç değer geçirebildiğini tahmin edemeyeceksiniz ve bu da büyük bir sayı olabilir.  
  
- Yordamın mantığı, çağıran kodun geçtiği tüm değerlerle yinelemesine, temelde her değer üzerinde aynı işlemleri gerçekleştirmenize olanak sağlar.  
  
 Daha fazla bilgi için bkz. [parametre dizileri](./parameter-arrays.md).  
  
## <a name="implicit-overloads-for-optional-parameters"></a>Isteğe bağlı parametreler için örtük aşırı yüklemeler  

 [Isteğe bağlı](../../../language-reference/modifiers/optional.md) parametresine sahip bir yordam, biri isteğe bağlı parametre ve diğeri olmadan olan iki aşırı yüklenmiş yordama eşdeğerdir. Bu tür bir yordamı, bunlardan birine karşılık gelen bir parametre listesi ile aşırı yükleyemezsiniz. Aşağıdaki bildirimlerde bu gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 Birden fazla isteğe bağlı parametreye sahip bir yordam için, önceki örnekteki şuna benzer şekilde, mantığa göre gelen bir dizi örtük aşırı yükleme vardır.  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>ParamArray parametresi için örtük aşırı yüklemeler  

 Derleyici, bir [ParamArray](../../../language-reference/modifiers/paramarray.md) parametresi ile bir yordamı, çağıran kodun parametre dizisine ne kadar başarılı bir şekilde (örneğin, aşağıdaki şekilde) geçirdiklerinde farklılık gösteren sınırsız sayıda aşırı yüklemeye sahip olacak şekilde değerlendirir:  
  
- Çağıran kodun bir bağımsız değişken sağlaması için bir aşırı yüklemesi `ParamArray`  
  
- Çağıran kod, öğe türünde tek boyutlu bir dizi sağladığı zaman için bir aşırı yükleme `ParamArray`  
  
- Her pozitif tamsayı için, çağıran kod bu sayıda bağımsız değişken sağladığı zaman için bir aşırı yükleme, her biri `ParamArray` öğe türü  
  
 Aşağıdaki bildirimlerde bu örtük aşırı yüklemeler gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Parametre dizisi için tek boyutlu bir dizi alan bir parametre listesiyle bu tür bir yordamı aşırı yükleyemezsiniz. Ancak, diğer örtük aşırı yüklemelerin imzalarını kullanabilirsiniz. Aşağıdaki bildirimlerde bu gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>Aşırı yükleme için alternatif olarak Türsüz programlama  

 Çağıran kodun bir parametreye farklı veri türleri geçirmeye izin vermek istiyorsanız, alternatif bir yaklaşım türsüz bir programdır. Tür denetimi anahtarını, `Off` [Strict ifadesiyle](../../../language-reference/statements/option-strict-statement.md) veya [-OptionStrict](../../../reference/command-line-compiler/optionstrict.md) derleyici seçeneğiyle olarak ayarlayabilirsiniz. Daha sonra parametrenin veri türünü bildirmeniz gerekmez. Ancak bu yaklaşım, aşırı yükleme ile karşılaştırıldığında aşağıdaki dezavantajlara sahiptir:  
  
- Türsüz programlama daha az verimli yürütme kodu üretir.  
  
- Yordamın anticipates geçirildiği her veri türü için test olması gerekir.  
  
- Çağıran kod, yordamın desteklemediği bir veri türünü geçerse derleyici bir hata sinyalini alamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)
- [Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)
- [Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma](./how-to-call-an-overloaded-procedure.md)
- [Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aşırı yükleme çözümlemesi](./overload-resolution.md)
- [Aşırı Yüklemeler](../../../language-reference/modifiers/overloads.md)
