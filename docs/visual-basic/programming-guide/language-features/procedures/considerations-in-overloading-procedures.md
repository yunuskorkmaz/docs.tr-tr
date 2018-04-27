---
title: Yordamları Aşırı Yüklemeye İlişkin Düşünceler (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ac4bc47f9e781f83c7930efffedd40d9c25c2ec2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>Yordamları Aşırı Yüklemeye İlişkin Düşünceler (Visual Basic)
Bir yordamı aşırı yükleme, farklı bir kullanmalısınız *imza* aşırı yüklenmiş her sürüm için. Bu, genellikle her sürümü farklı parametre listesi belirtmelisiniz anlamına gelir. Daha fazla bilgi için bkz: "Farklı imza" [yordam aşırı yüklemesi](./procedure-overloading.md).  
  
 Aşırı yüklenebilir bir `Function` yordamla bir `Sub` yordamı ve bunun tersini yapmak, sahip oldukları farklı imzalar sağlanan. İki aşırı yalnızca bir dönüş değeri varsa ve diğer desteklemez, farklı olamaz.  
  
 Bir yordamı aşırı yükleme aynı şekilde bir özellik aşırı yüklenebilir ve aynı kısıtlamalara sahip. Bir yordamı aşırı yükleme olamaz ancak, bir özellik veya tersi.  
  
## <a name="alternatives-to-overloaded-versions"></a>Aşırı yüklenmiş sürümleri alternatifleri  
 Özellikle bağımsız değişken varlığını isteğe bağlı olduğunda veya numarasına değişkenidir bazen aşırı yüklenmiş sürümlere seçeneğiniz vardır.  
  
 İsteğe bağlı bağımsız değişkenler mutlaka tüm diller tarafından desteklenmez ve parametre dizileri Visual Basic'e sınırlı aklınızda bulundurun. Birkaç farklı dildeki hiçbirinde yazılan kod öğesinden çağrılması büyük olasılıkla bir yordam yazıyorsanız sürümleri teklif en büyük esnekliği aşırı yüklendi.  
  
### <a name="overloads-and-optional-arguments"></a>Aşırı ve isteğe bağlı bağımsız değişkenler  
 Çağrıyı yapan kod, isteğe bağlı olarak sağlayın veya bağımsız değişkenlerden biri veya daha fazla atlarsanız, birden çok aşırı yüklü sürümlerini tanımlamak veya isteğe bağlı parametreler kullanın.  
  
#### <a name="when-to-use-overloaded-versions"></a>Ne zaman kullanılacağı sürümleri aşırı yüklenmiş  
 Aşağıdaki durumlarda aşırı yüklenmiş sürümlerinin bir dizi tanımlamayı düşünebilirsiniz:  
  
-   Yordam kodu mantık olup çağıran kodu isteğe bağlı bir bağımsız değişken veya sağlayan bağlı olarak önemli ölçüde farklıdır.  
  
-   Çağıran kodu isteğe bağlı bir bağımsız değişken sağlanan olup olmadığını yordamı kodu güvenilir bir şekilde test edilemez. Bu durumda, yoksa hiçbir olası adayı varsayılan bir değer için örneğin, çağrıyı yapan kod sağlamak için beklenebilir değil.  
  
#### <a name="when-to-use-optional-parameters"></a>Ne zaman isteğe bağlı parametreler kullanılır  
 Bir veya daha fazla isteğe bağlı parametreler aşağıdaki durumlarda tercih edebilirsiniz:  
  
-   Çağrıyı yapan kod isteğe bağlı bir bağımsız değişken sağlayın değil, yalnızca gerekli parametre için varsayılan bir değer ayarlamak için eylemdir. Bir veya daha fazla tek sürümü tanımlarsanız, böyle bir durumda yordamı kod daha az karmaşık olabilir `Optional` parametreleri.  
  
 Daha fazla bilgi için bkz: [isteğe bağlı parametreler](./optional-parameters.md).  
  
### <a name="overloads-and-paramarrays"></a>Aşırı ve ParamArrays  
 Çağıran kodu değişken sayıda bağımsız değişken geçirdiğinizde birden çok aşırı yüklü sürümlerini tanımlamak ya da bir parametre dizisi kullanın.  
  
#### <a name="when-to-use-overloaded-versions"></a>Ne zaman kullanılacağı sürümleri aşırı yüklenmiş  
 Aşağıdaki durumlarda aşırı yüklenmiş sürümlerinin bir dizi tanımlamayı düşünebilirsiniz:  
  
-   Çağrıyı yapan kod hiçbir zaman birden çok az sayıda değerleri parametre dizisine geçtiğini bildiğiniz.  
  
-   Yordam kodu mantık çağıran kodu geçirir kaç değerleri bağlı olarak önemli ölçüde farklıdır.  
  
-   Çağrıyı yapan kod farklı veri türlerini değerlerinin geçmesini sağlayabilirsiniz.  
  
#### <a name="when-to-use-a-parameter-array"></a>Bir parametre dizisi kullanma zamanı  
 Daha iyi tarafından sunulan bir `ParamArray` aşağıdaki durumlarda parametre:  
  
-   Çağrıyı yapan kod parametre dizisine geçirebilirsiniz kaç değerleri tahmin etmek mümkün değildir ve büyük bir sayı olabilir.  
  
-   Yordam mantığı kendisini çağıran kodu geçirir, her değer üzerinde temelde aynı işlemler tüm değerler üzerinden yineleme için uygundur.  
  
 Daha fazla bilgi için bkz: [parametre dizileri](./parameter-arrays.md).  
  
## <a name="implicit-overloads-for-optional-parameters"></a>İsteğe bağlı parametreler için örtük aşırı yüklemeleri  
 Bir yordama bir [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md) parametresi, bir isteğe bağlı bir parametre ve olmadan bir olmak üzere iki aşırı yüklenmiş yordamları eşdeğerdir. Bunlardan birisi karşılık gelen bir parametre listesi ile bu tür bir yordamı aşırı yükleme yapılamıyor. Aşağıdaki bildirimler bu gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 Birden fazla isteğe bağlı bir parametre ile bir yordam için örtük aşırı yüklemeleri, önceki örnekte benzer mantığı tarafından gelen kümesi yok.  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>ParamArray parametresi için örtük aşırı yüklemeleri  
 Bir yordama derleyici göz önünde bulundurur bir [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) ne çağıran kodu parametre dizisine gibi geçirir birbirinden farklı bir aşırı yüklemeleri, sonsuz sayıda sahip parametre:  
  
-   Ne zaman çağıran kodu bir bağımsız değişken sağlamıyor için aşırı yüklemesiyle `ParamArray`  
  
-   Ne zaman tek boyutlu dizi çağıran kodu sağlıyor için aşırı yüklemesiyle `ParamArray` öğe türü  
  
-   Her bir pozitif tamsayı için bir aşırı yükleme için bu bağımsız değişken sayısı, her biri çağıran kodu sağlıyor zaman `ParamArray` öğe türü  
  
 Aşağıdaki bildirimler bu örtük aşırı yüklemeleri gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 Tek boyutlu bir dizi parametre dizisi için gereken bir parametre listesi ile bu tür bir yordamı aşırı yükleme yapılamıyor. Ancak, diğer örtük aşırı imzalarını kullanabilirsiniz. Aşağıdaki bildirimler bu gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>Aşırı yükleme alternatif olarak yazısız programlama  
 Veri türleri farklı bir parametreye geçirmek üzere çağıran kodu izin vermek istiyorsanız, alternatif bir yaklaşım yazısız programlama ' dir. Tür anahtara denetleme ayarlayabilirsiniz `Off` ya da ile [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) veya [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) derleyici seçeneği. Ardından parametre veri türü belirtmesi gerekmez. Ancak, bu yaklaşım aşırı yüklemesi için kıyasla aşağıdaki dezavantajları bulunur:  
  
-   Yazısız programlama daha az verimli yürütme kodu oluşturur.  
  
-   Yordam geçirilen düşünmektedir her veri türü için test etmeniz gerekir.  
  
-   Derleyici arama kodu yordamı desteği olmayan bir veri türü geçirir, bir hata sinyal olamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamlar](./index.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)  
 [Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma](./how-to-call-an-overloaded-procedure.md)  
 [Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Aşırı Yükleme Çözümü](./overload-resolution.md)  
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
