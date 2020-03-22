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
ms.openlocfilehash: 84d52bbbfb34c2e5d67ed6a1810ab3e32fafda22
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266878"
---
# <a name="overload-resolution-visual-basic"></a>Aşırı Yükleme Çözümü (Visual Basic Başvurusu)
Visual Basic derleyicisi, aşırı yüklü birkaç sürümde tanımlanan bir yordam için bir çağrıyla karşılaştığında, derleyici nin hangi aşırı yüklemeden arayacağına karar vermesi gerekir. Bunu aşağıdaki adımları gerçekleştirerek yapar:  
  
1. **Erişilebilir -lik.** Arama kodunun aramasını engelleyen bir erişim düzeyine sahip aşırı yüklemeyi ortadan kaldırır.  
  
2. **Parametrelerin Sayısı.** Çağrıda verilenden farklı sayıda parametre tanımlayan aşırı yüklemeyi ortadan kaldırır.  
  
3. **Parametre Veri Türleri.** Derleyici, örnek yöntemleri ni genişletme yöntemlerine göre tercih sağlar. Yordam çağrısıyla eşleşecek şekilde yalnızca genişletme dönüşümleri gerektiren herhangi bir örnek yöntemi bulunursa, tüm uzantı yöntemleri bırakılır ve derleyici yalnızca örnek yöntemi adaylarıyla devam eder. Böyle bir örnek yöntemi bulunamazsa, hem örnek hem de uzantı yöntemleriyle devam e-devam edin.  
  
     Bu adımda, arama bağımsız değişkenlerinin veri türlerinin aşırı yükte tanımlanan parametre türlerine dönüştürülemeyeceği aşırı yüklemeyi ortadan kaldırır.  
  
4. **Dönüşümleri Daraltma.** Çağrı bağımsız değişkeni türlerinden tanımlı parametre türlerine daraltma dönüştürme gerektiren aşırı yüklemeyi ortadan kaldırır. Bu, tür kontrol anahtarının[(Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) veya `On` . `Off`  
  
5. **En az genişletme.** Derleyici, kalan aşırı yüklemeleri çiftler halinde dikkate alır. Her çift için, tanımlanan parametrelerin veri türlerini karşılaştırır. Aşırı yüklerden birinde bulunan türler diğerindeki karşılık gelen türlere genişlerse, derleyici ikincisini ortadan kaldırır. Diğer bir süre, en az genişletme gerektiren aşırı yükü korur.  
  
6. **Tek Aday.** Yalnızca bir aşırı yükleme kalana kadar çiftler halinde aşırı yüklemeleri göz önünde bulundurmaya devam eder ve aşırı yükleme çağrısını çözer. Derleyici aşırı yüklemeleri tek bir adaya indiremiyorsa, bir hata oluşturur.  
  
 Aşağıdaki resimde, aşırı yüklü sürümler kümesinden hangisinin çağrılmasını belirleyen işlem gösterilmektedir.  
  
 ![Aşırı yük çözümleme işleminin akış diyagramı](./media/overload-resolution/determine-overloaded-version.gif "Aşırı yüklü sürümler arasında çözme")
  
 Aşağıdaki örnek, bu aşırı yük çözümleme işlemini göstermektedir.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 İlk çağrıda derleyici ilk aşırı yükü ortadan kaldırır, çünkü ilk`Short`bağımsız değişkenin ( ) türü karşılık`Byte`gelen parametrenin türüne daralır ( ). İkinci aşırı yükteki her bağımsız değişken türü (ve)`Short` `Single`üçüncü aşırı yükte (ve) `Single`karşılık gelen`Integer` türe genişlediği için üçüncü aşırı yükü ortadan kaldırır. İkinci aşırı yükleme daha az genişletme gerektirir, bu nedenle derleyici arama için kullanır.  
  
 İkinci çağrıda, derleyici daralma temelinde aşırı yüklerin hiçbirini ortadan kaldıramaz. Bağımsız değişken türlerinin daha az genişletilmesi yle ikinci aşırı yüklemeyi çağırabildiği için, ilk çağrıdaki yle aynı nedenle üçüncü aşırı yüklemeyi ortadan kaldırır. Ancak, derleyici birinci ve ikinci aşırı yüklemeler arasında çözemez. Her biri, diğerinde karşılık gelen türe`Byte` (to `Short`, ama) `Double` `Single` genişleyen tanımlanmış bir parametre türüne sahiptir. Derleyici bu nedenle aşırı yük çözümlü hata oluşturur.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Aşırı Yüklü İsteğe Bağlı ve ParamArray Bağımsız Değişkenleri  
 Bir yordamın iki aşırı yükü, son parametrenin birinde [Isteğe Bağlı,](../../../../visual-basic/language-reference/modifiers/optional.md) diğerinde [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) olarak beyan edildiği dışında aynı imzalara sahipse, derleyici bu yordamiçin bir çağrıyı aşağıdaki gibi çözer:  
  
|Arama son bağımsız değişkeni|Derleyici, son bağımsız değişkeni bildiren aşırı yüke çağrıyı çözer|  
|---|---|  
|Değer yok (bağımsız değişken atlandı)|`Optional`|  
|Tek bir değer|`Optional`|  
|Virgülle ayrılmış bir listede iki veya daha fazla değer|`ParamArray`|  
|Herhangi bir uzunlukta bir dizi (boş bir dizi dahil)|`ParamArray`|  
  
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
- [Aşırı Yüklemeler](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Genişletme Yöntemleri](./extension-methods.md)
