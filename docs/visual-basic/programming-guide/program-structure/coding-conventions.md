---
title: Visual Basic Kodlama Kuralları
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: b686747b46529b53b0802a7deb38b5b4949f4d5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655367"
---
# <a name="visual-basic-coding-conventions"></a>Visual Basic Kodlama Kuralları
Microsoft, örnekler ve bu konudaki yönergeleri izleyin belgeler geliştirir. Aynı kodlama kurallarını izlerseniz, aşağıdaki faydaları elde:  
  
-   Okuyucular değil düzeni içeriğe göre daha iyi odaklanabilmeniz için kodunuzu tutarlı bir görünüm sahip olur.  
  
-   Önceki deneyimleri temel varsayımları yapabilirsiniz çünkü okuyucular kodunuzu daha hızlı bir şekilde anlayın.  
  
-   Kopyalama, değiştirmek ve kodu daha kolay korumak.  
  
-   Kodunuz için Visual Basic "en iyi yöntemleri" gösteren sağlamaya yardımcı olur.  
  
## <a name="naming-conventions"></a>Adlandırma kuralları  
  
-   Adlandırma kuralları hakkında daha fazla bilgi için bkz: [adlandırma yönergeleri](../../../standard/design-guidelines/naming-guidelines.md) konu.  
  
-   "Belgelerim" veya "benim" bir değişken adı bir parçası olarak kullanmayın. Bu yöntem security'deki oluşturur `My` nesneleri.  
  
-   Kodda bunları yönergelerine uygun hale getirmek için otomatik olarak oluşturulan nesnelerin adlarını değiştirmek zorunda değildir.  
  
## <a name="layout-conventions"></a>Düzeni Kuralları  
  
-   Sekme alanları olarak ekleyin ve akıllı ile dört alanı girintileri girintileme kullanın.  
  
-   Kullanım **oldukça (, yeniden biçimlendirme) kod listesi** kodunuzu Kod düzenleyicisinde yeniden biçimlendirmek için. Daha fazla bilgi için bkz: [seçenekler, metin düzenleyici, temel (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
-   Satır başına yalnızca bir deyim kullanın. Visual Basic satır ayırıcı karakteri (:) kullanmayın.  
  
-   Dil veren her yerde örtük satır devamlılığı lehinde açık satır devamlılığı karakteri "_" kullanmaktan kaçının.  
  
-   Satır başına yalnızca bir bildirimi kullanın.  
  
-   Varsa **oldukça (, yeniden biçimlendirme) kod listesi** biçimi devamlılık satırları otomatik olarak, el ile devamlılık satırları bir sekme durağı girinti değil. Bununla birlikte, her zaman sol listedeki öğeleri Hizala.  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   Yöntem ve özellik tanımları arasında en az bir boş satır ekleyin.  
  
## <a name="commenting-conventions"></a>Yorum Oluşturma Kuralları  
  
-   Yerine ayrı bir satırda kod satırının sonunda açıklamaları yerleştirin.  
  
-   Açıklama metni büyük harfe ile ve bir süre sonu yorum metni başlatın.  
  
-   Açıklama sınırlayıcısı (') ve bir açıklama metni arasında bir boşluk ekler.  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   Yıldız işareti biçimlendirilmiş bloklarını yorumlarla çevreleyen değil.  
  
## <a name="program-structure"></a>Program Yapısı  
  
-   Kullandığınızda `Main` yöntemi, varsayılan yapı için yeni konsol uygulamaları kullanıyorsanız ve `My` komut satırı bağımsız değişkenleri için.  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a>Dil Kuralları  
  
### <a name="string-data-type"></a>Dize Veri Türü  
  
-   Dizeyi birleştirmek için ve işareti kullanın (&).  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   Döngüler dizelerde eklemek için kullanın <xref:System.Text.StringBuilder> nesnesi.  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Gevşek temsilci olay işleyicileri  
 Açıkça bağımsız değişkenleri (nesne ve EventArgs) olay işleyicileri için uygun değil. Bir olay (örneğin, gönderen e EventArgs olarak nesnesi olarak) için geçirilen olay bağımsız değişkenlerinin kullanmıyorsanız, gevşek temsilci kullanın ve olay bağımsız değişkenlerinin kodunuzda çıkışı bırakın:  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a>İmzasız Veri Türü  
  
-   Kullanım `Integer` gerekli olduğu dışında imzasız türler yerine.  
  
### <a name="arrays"></a>Diziler  
  
-   Diziler bildirimi satırındaki başlattığınızda kısa sözdizimini kullanın. Örneğin, aşağıdaki sözdizimini kullanın.  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     Aşağıdaki sözdizimini kullanmayın.  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   Dizi Belirleyicisi türünde, değişkeni üzerinde yerleştirin. Örneğin, aşağıdaki sözdizimini kullanın:  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     Aşağıdaki sözdizimini kullanmayın:  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   Bildirme ve temel veri türlerinin dizileri başlatma {} sözdizimini kullanın. Örneğin, aşağıdaki sözdizimini kullanın:  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     Aşağıdaki sözdizimini kullanmayın:  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a>Kullanım anahtar sözcüğü ile  
 Bir dizi bir nesneye çağrısı yaptığınızda, kullanmayı `With` anahtar sözcüğü:  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>İçin try... Catch ve kullanarak özel durum işleme kullandığınızda deyimleri  
 Kullanmayın `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>IsNot anahtar sözcüğünü kullanın  
 Kullanım `IsNot` anahtar sözcüğü yerine `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>New anahtar sözcüğü  
  
-   Kısa örneklemesi kullanın. Örneğin, aşağıdaki sözdizimini kullanın:  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     Önceki satır için eşdeğerdir:  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   Nesne başlatıcıları parametresiz bir kurucusu yerine yeni nesneler için kullanın:  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a>Olay İşleme  
  
-   Kullanım `Handles` yerine `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   Kullanım `AddressOf`ve temsilci açıkça örneği değil:  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   Bir olay tanımladığınızda, kısa söz dizimini kullanın ve temsilci tanımlamak derleyici sağlar:  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   Bir olay olup olmadığını doğrulamaz `Nothing` (çağırmadan önce null) `RaiseEvent` yöntemi. `RaiseEvent` denetler `Nothing` olayı oluşturmadan önce.  
  
### <a name="using-shared-members"></a>Paylaşılan üyeler kullanma  
 Çağrı `Shared` bir örnek değişkeni değil, sınıf adı kullanarak üyeleri.  
  
### <a name="use-xml-literals"></a>XML değişmez değerleri  
 XML değişmez değerleri (örneğin, yükleme, sorgu ve dönüştürme) XML ile çalışırken karşılaştığınız en yaygın görevleri basitleştirin. XML ile geliştirirken, aşağıdaki yönergeleri izleyin:  
  
-   XML değişmez değerleri XML belgelerini ve XML API'lerini doğrudan çağırmak yerine parçalarını oluşturmak için kullanın.  
  
-   XML değişmez değerleri için performans iyileştirmelerinden yararlanmasını için dosya veya proje düzeyinde XML ad alanlarını içeri aktarın.  
  
-   XML eksen özellikleri öğeleri ve özniteliklerinin bir XML belgesi erişmek için kullanın.  
  
-   Katıştırılmış ifadeler değerleri dahil etmek ve XML API çağrıları gibi kullanmak yerine var olan değerleri oluşturmak için kullanın `Add` yöntemi:  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a>LINQ Sorguları  
  
-   Sorgu değişkenleri için anlamlı adlar kullanın:  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   Pascal kullanarak anonim türdeki özellik adlarının doğru olduğundan emin olmak için bir sorgu öğe adı sağlayan büyük/küçük harf:  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   Özellik adlarının sonuç belirsiz kullanırken özellikleri yeniden adlandırın. Sorgunuzu adı ve bir sipariş kimliği müşteri döndürürse, örneğin, bunları olarak bırakarak yerine adlandırabilir `Name` ve `ID` sonuç:  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   Tür çıkarımı sorgu değişkenleri ve aralık değişkeni bildiriminde kullanın:  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   Sorgu yan tümceleri altında Hizala `From` deyimi:  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   Kullanım `Where` yan tümceleri diğer önce sorgu yan tümceleri böylece sonraki sorgu yan tümceleri filtrelenmiş veri kümesi üzerinde çalışır:  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   Kullanım `Join` açıkça kullanmak yerine bir birleştirme işlemi tanımlamak için yan tümcesi `Where` örtük olarak bir birleştirme işlemi tanımlamak için yan tümcesi:  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli Kodlama Yönergeleri](../../../standard/security/secure-coding-guidelines.md)
