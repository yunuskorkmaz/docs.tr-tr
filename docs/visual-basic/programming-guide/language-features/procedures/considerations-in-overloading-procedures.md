---
title: Yordamları Aşırı Yüklemeye İlişkin Düşünceler (Visual Basic)
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
ms.openlocfilehash: 234cd23c487f92cfa1e2761dd7a6caadf8820704
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685808"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>Yordamları Aşırı Yüklemeye İlişkin Düşünceler (Visual Basic)
Bir yordamı aşırı yükleme, farklı bir kullanmalısınız *imza* aşırı yüklü her sürüm için. Bu, genellikle her sürüm başka bir parametre listesi belirtmelisiniz anlamına gelir. Daha fazla bilgi için bkz: "Farklı imza" [yordam aşırı yüklemesi](./procedure-overloading.md).  
  
 Aşırı yüklenme olabilir bir `Function` yordamla bir `Sub` yordamı ve bunun tersi de farklı imzalara sahip oldukları sağlanır. İki aşırı yüklemesi, yalnızca bir dönüş değeri varsa ve diğer yok farklılık göstermeyebilir.  
  
 Bir yordamı aşırı yükleme aynı şekilde bir özelliği aşırı yükleyebilirsiniz ve aynı kısıtlamalara sahip. Bir yordamı aşırı yükleme olamaz ancak, bir özellik veya bunun tersi de geçerlidir.  
  
## <a name="alternatives-to-overloaded-versions"></a>Aşırı yüklenmiş sürümleri alternatifleri  
 Özellikle isteğe bağlı bağımsız değişkenler varlığını veya numarasına değişkeni bazen aşırı yüklenmiş sürümleri seçeneğiniz vardır.  
  
 İsteğe bağlı bağımsız değişkenlere mutlaka tüm diller tarafından desteklenmez ve Visual Basic parametre dizileri sınırlıdır aklınızda bulundurun. Birkaç farklı dildeki hiçbirinde yazılan kodundan çağrılmak büyük olasılıkla bir yordam yazıyorsanız, en büyük esnekliği sürümleri teklif aşırı.  
  
### <a name="overloads-and-optional-arguments"></a>İsteğe bağlı bağımsız değişkenler ve aşırı yüklemeler  
 Çağıran kod, isteğe bağlı olarak sağlamak veya bir veya daha fazla bağımsız değişken çıkarın, birden fazla aşırı yüklü sürümler tanımlayın veya isteğe bağlı parametreler kullanın.  
  
#### <a name="when-to-use-overloaded-versions"></a>Ne zaman aşırı yüklenmiş sürümleri kullanın  
 Aşağıdaki durumlarda bir dizi aşırı yüklü sürümlerini tanımlama düşünebilirsiniz:  
  
-   Yordam kodunda mantığı olup çağrıldığı koda bir isteğe bağlı bağımsız değişkeni veya sağlar bağlı olarak önemli ölçüde farklılık gösterir.  
  
-   Yordam kodu güvenilir bir şekilde çağıran kod tarafından sağlanan bağımsız değişken isteğe bağlı olup olmadığını test edilemez. Bu durumda, yoksa hiçbir olası aday varsayılan bir değer için örneğin, çağıran kodun sağlamak için beklenebilir değil.  
  
#### <a name="when-to-use-optional-parameters"></a>Olduğunda isteğe bağlı parametreler kullanılacak  
 Bir veya daha fazla isteğe bağlı parametreler aşağıdaki durumlarda tercih edebilirsiniz:  
  
-   Çağıran kod, isteğe bağlı bağımsız değişken sağlamıyor çalıştırıldığında yalnızca gerekli eylem parametresi varsayılan değerine ayarlamaktır. Bir veya daha fazla tek bir sürüm tanımlarsanız, böyle bir durumda yordamının kodunu daha az karmaşık olabilir `Optional` parametreleri.  
  
 Daha fazla bilgi için [isteğe bağlı parametreler](./optional-parameters.md).  
  
### <a name="overloads-and-paramarrays"></a>ParamArrays ve aşırı yüklemeler  
 Çağıran kod, değişken sayıda bağımsız değişken geçirebilirsiniz, birden fazla aşırı yüklü sürümler tanımlayın veya bir parametre dizisi kullanın.  
  
#### <a name="when-to-use-overloaded-versions"></a>Ne zaman aşırı yüklenmiş sürümleri kullanın  
 Aşağıdaki durumlarda bir dizi aşırı yüklü sürümlerini tanımlama düşünebilirsiniz:  
  
-   Çağıran kod hiçbir zaman birden çok az sayıda değerler için parametre dizisi geçen biliyor.  
  
-   Yordam kodunda mantığı çağıran kod geçirir kaç değerlerine bağlı olarak önemli ölçüde farklılık gösterir.  
  
-   Çağıran kod, farklı veri türleri değerlerinin geçmesini sağlayabilirsiniz.  
  
#### <a name="when-to-use-a-parameter-array"></a>Ne zaman bir parametre dizisi kullanılır?  
 Daha iyi tarafından sunulan bir `ParamArray` parametre aşağıdaki durumlarda:  
  
-   Çağıran kod için parametre dizisi geçirebilirsiniz kaç değer tahmin etmek mümkün değildir ve büyük bir sayı olabilir.  
  
-   Yordam mantıksal kendisini çağıran kod geçirir, her değer esas olarak aynı işlemleri gerçekleştirmek tüm değerleri üzerinden yineleme için uygundur.  
  
 Daha fazla bilgi için [parametre dizileri](./parameter-arrays.md).  
  
## <a name="implicit-overloads-for-optional-parameters"></a>İsteğe bağlı parametreler için örtük aşırı yüklemeleri  
 Bir yordamı bir [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) parametresi, bir isteğe bağlı parametre içeren ve olmadan bir tane olmak üzere iki aşırı yüklenmiş yordam eşdeğerdir. Bunlardan biri için karşılık gelen bir parametre listesi ile bu tür bir yordamı aşırı yükleme yapılamıyor. Aşağıdaki bildirimleri bu göstermektedir.  
  
 [!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 Birden fazla isteğe bağlı parametre içeren bir yordam için örtük aşırı yüklemeleri, önceki örnekte benzer mantığı tarafından gelen bir dizi yoktur.  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>Bir ParamArray parametresiyle için örtük aşırı yüklemeleri  
 Derleyici bir yordama göz önünde bulundurur bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) ne çağıran kod parametre dizisine gibi geçirir birbirinden farklı aşırı yüklemeler, sonsuz bir sayıda parametre:  
  
-   Ne zaman çağıran kodu bir bağımsız değişken sağlamıyor için bir aşırı yükleme `ParamArray`  
  
-   Çağıran kod tek boyutlu bir dizi zaman kaynakları için bir aşırı `ParamArray` öğe türü  
  
-   Her bir pozitif tamsayı için bir aşırı yükleme için çağıran kod sağlar, her biri bağımsız değişken sayısı olduğunda `ParamArray` öğe türü  
  
 Aşağıdaki bildirimleri bu örtük aşırı yüklemeler göstermektedir.  
  
 [!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 Böyle bir yordam bir parametre listesiyle parametre dizisi için tek boyutlu bir dizi alan aşırı yükleyemez. Ancak, bir örtük aşırı imzalarını kullanabilirsiniz. Aşağıdaki bildirimleri bu göstermektedir.  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>Aşırı yükleme alternatif olarak yazısız programlama  
 Farklı veri türleri için bir parametre geçirmek çağıran kod izin vermek istiyorsanız, alternatif bir yaklaşım yazısız programlama ' dir. Tür denetleme anahtara ayarlayabilirsiniz `Off` ya da ile [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) veya [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) derleyici seçeneği. Ardından parametrenin veri türü bildirmek gerekmez. Ancak, bu yaklaşım, aşırı yüklemesi için kıyasla aşağıdaki dezavantajları bulunur:  
  
-   Yazısız programlama yürütme daha az verimli kod üretir.  
  
-   Yordamı, geçirilen düşünmektedir her veri türü için test etmeniz gerekir.  
  
-   Derleyici çağıran kod yordamı desteklemediği bir veri türü geçerse hata sinyali vermek olamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)
- [Nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)
- [Nasıl yapılır: Aşırı yüklenmiş bir yordamı çağırma](./how-to-call-an-overloaded-procedure.md)
- [Nasıl yapılır: İsteğe bağlı parametreler isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Nasıl yapılır: Belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aşırı Yükleme Çözümü](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
