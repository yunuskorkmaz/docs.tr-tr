---
title: Aşırı Yükleme Çözümü
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
ms.openlocfilehash: 9b83eba8efc8dfe14b6ec1cbab270984977198e5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071371"
---
# <a name="overload-resolution-visual-basic"></a>Aşırı Yükleme Çözümü (Visual Basic Başvurusu)

Visual Basic derleyici, birkaç aşırı yüklenmiş sürümde tanımlanan bir yordama bir çağrı ile karşılaştığında, derleyicinin hangi aşırı yükleme için çağrılacağını karar vermelidir. Bunu aşağıdaki adımları gerçekleştirerek yapar:  
  
1. **Erişilebilirlik.** Çağırma kodunun çağırmasının önlediği bir erişim düzeyine sahip tüm aşırı yüklemeleri ortadan kaldırır.  
  
2. **Parametre sayısı.** Çağrıda sağlanenden farklı sayıda parametre tanımlayan aşırı yüklemeleri ortadan kaldırır.  
  
3. **Parametre veri türleri.** Derleyici, uzantı yöntemleri üzerinde örnek yöntemleri tercihi sağlar. Yordam çağrısını eşleştirmek için yalnızca genişletme dönüştürmeleri gerektiren herhangi bir örnek yöntemi bulunursa, tüm uzantı yöntemleri bırakılır ve derleyici yalnızca örnek yöntemi adaylarıyla devam eder. Böyle bir örnek yöntemi bulunamazsa, hem örnek hem de uzantı yöntemleriyle devam eder.  
  
     Bu adımda, çağıran bağımsız değişkenlerin veri türlerinin aşırı yüklemede tanımlanan parametre türlerine dönüştürülemediği tüm aşırı yüklemeleri ortadan kaldırır.  
  
4. **Daraltma dönüştürmeleri.** Çağıran bağımsız değişken türlerinden tanımlanan parametre türlerine daraltma dönüştürmesi gerektiren tüm aşırı yüklemeleri ortadan kaldırır. Bu, tür denetimi anahtarı ([Option Strict deyimin](../../../language-reference/statements/option-strict-statement.md)) veya ' nin olup olmadığı doğrudur `On` `Off` .  
  
5. **En az genişletme.** Derleyici, kalan aşırı yüklerini çiftler halinde dikkate alır. Her çift için, tanımlanan parametrelerin veri türlerini karşılaştırır. Aşırı yüklerden birindeki türlerin tümü, diğer içindeki ilgili türlere genişletürde, derleyici ikincisini ortadan kaldırır. Yani, en az genişletme miktarı gerektiren aşırı yüklemeyi korur.  
  
6. **Tek aday.** Yalnızca bir aşırı yükleme kalana kadar çiftlerin çiftler halinde düşünülmeye devam eder ve bu aşırı yüklemeye çağrı çözülür. Derleyici, aşırı yüklerini tek bir aday olarak azaltamaz bir hata üretir.  
  
 Aşağıdaki çizimde, bir dizi aşırı yüklenmiş sürüm çağrısını belirleyen işlem gösterilmektedir.  
  
 ![Aşırı yükleme çözümleme işleminin akış diyagramı](./media/overload-resolution/determine-overloaded-version.gif "Aşırı yüklenmiş sürümler arasında çözümleme")
  
 Aşağıdaki örnekte bu aşırı yükleme çözümleme süreci gösterilmektedir.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 İlk çağrıda derleyici ilk tekrar yüklemeyi ortadan kaldırır çünkü ilk bağımsız değişkenin türü ( `Short` ), karşılık gelen parametrenin türüne () göre daraltır `Byte` . İkinci aşırı yükteki (ve) her bağımsız değişken türü `Short` `Single` üçüncü aşırı yüklemede karşılık gelen türe (ve) widens için, daha sonra üçüncü aşırı yüklemeyi ortadan kaldırır `Integer` `Single` . İkinci aşırı yükleme daha az genişletme gerektirir, bu nedenle derleyici onu çağrı için kullanır.  
  
 İkinci çağrıda, derleyici daraltma temelinde aşırı yüklemelerin hiçbirini ortadan kaldırmaz. İkinci aşırı yükleme, bağımsız değişken türlerini daha az genişletme ile çağırabildiğinden, birinci çağrıdan itibaren aynı nedenden dolayı üçüncü aşırı yüklemeyi ortadan kaldırır. Ancak, derleyici birinci ve ikinci aşırı yüklemeler arasında çözümlenemez. Her biri, diğer ( `Byte` `Short` , ancak `Single` için) öğesine karşılık gelen türe widens bir tanımlı parametre türüne sahiptir `Double` . Bu nedenle derleyici aşırı yükleme çözümlemesi hatası oluşturur.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Aşırı yüklenmiş Isteğe bağlı ve ParamArray bağımsız değişkenleri  

 Bir yordamın iki aşırı yüklemesi aynı imzaya sahip ise, son parametrenin diğer bir ve [ParamArray](../../../language-reference/modifiers/paramarray.md) 'de [isteğe bağlı](../../../language-reference/modifiers/optional.md) olarak bildirildiği durumlar dışında, derleyici aşağıdaki gibi bu yordama bir çağrı çözer:  
  
|Çağrı son bağımsız değişkeni şu şekilde sağlar|Derleyici, son bağımsız değişkeni şu şekilde bildiren aşırı yükleme çağrısını çözer|  
|---|---|  
|Değer yok (bağımsız değişken atlandı)|`Optional`|  
|Tek bir değer|`Optional`|  
|Virgülle ayrılmış bir listede iki veya daha fazla değer|`ParamArray`|  
|Herhangi bir uzunlukta dizi (boş bir dizi dahil)|`ParamArray`|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İsteğe Bağlı Parametreler](./optional-parameters.md)
- [Parametre Dizileri](./parameter-arrays.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Yordam Sorunlarını Giderme](./troubleshooting-procedures.md)
- [Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)
- [Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma](./how-to-call-an-overloaded-procedure.md)
- [Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](./considerations-in-overloading-procedures.md)
- [Aşırı Yüklemeler](../../../language-reference/modifiers/overloads.md)
- [Uzantı Metotları](./extension-methods.md)
