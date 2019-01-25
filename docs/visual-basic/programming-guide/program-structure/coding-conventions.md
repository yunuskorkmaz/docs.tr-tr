---
title: Visual Basic Kodlama Kuralları
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: f2b1676ae959c5426af3021bbd340980115c5da6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724888"
---
# <a name="visual-basic-coding-conventions"></a>Visual Basic Kodlama Kuralları
Microsoft, örnekler ve bu konudaki yönergeleri izleyen belgeler geliştirir. Aynı kodlama kurallarını takip ederseniz, aşağıdaki faydaları elde edebilirsiniz:  
  
-   Okuyucular düzene değil içeriğe göre daha iyi odaklanabilmeniz için kodunuzu tutarlı bir görünüm olacaktır.  
  
-   Bunlar önceki deneyime dayanan varsayımlar yapabilecekleri için Okuyucular kodunuzu daha hızlı bir şekilde anlayın.  
  
-   Kopyalama, değiştirme ve kodu daha kolay korumak.  
  
-   Kodunuzu Visual Basic için "en iyi uygulamaları" göstermesini sağlamaya yardımcı olur.  
  
## <a name="naming-conventions"></a>Adlandırma kuralları  
  
-   Adlandırma yönergeleri hakkında daha fazla bilgi için bkz: [adlandırma yönergeleri](../../../standard/design-guidelines/naming-guidelines.md) konu.  
  
-   Bir değişken adının parçası olarak "My" veya "my" kullanmayın. Bu yöntem karışıklık oluşturur `My` nesneleri.  
  
-   Nesnelerin yönergelere sığması olacak şekilde otomatik olarak oluşturulan kod adlarını değiştirmeniz gerekmez.  
  
## <a name="layout-conventions"></a>Düzeni Kuralları  
  
-   Sekmeleri boşluk olarak ekleyin ve dört boşluklu akıllı girintileme kullanın.  
  
-   Kullanım **(yeniden biçimlendirme) kodu düzgün listeleme** Kod düzenleyicisinde kodunuzu yeniden biçimlendirmek için. Daha fazla bilgi için [seçenekler, metin düzenleyici, temel (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
-   Her satırda yalnızca bir deyim kullanın. Visual Basic Satır Ayırıcı karakterini (:) kullanmayın.  
  
-   Dil her izin verdiğinde örtük satır devamlılığı açık satır devamlılığı karakterini "_" kullanmaktan kaçının.  
  
-   Her satırda yalnızca bir bildirim kullanın.  
  
-   Varsa **(yeniden biçimlendirme) kodu düzgün listeleme** devamlılık satırlarını otomatik olarak, el ile devamlılık satırlarını bir sekme durağı girinti verin. Ancak, her zaman sola bir listedeki öğeler Hizala.  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   Yöntem ve özellik tanımları arasına en az bir boş satır ekleyin.  
  
## <a name="commenting-conventions"></a>Yorum Oluşturma Kuralları  
  
-   Açıklamaları bir kod satırının sonundaki yerine ayrı bir satıra yerleştirin.  
  
-   Son yorum metnini noktayla yanı sıra büyük harfle yorum metni başlatın.  
  
-   Açıklama sınırlayıcısı (') ve açıklama metni arasına tek boşluk ekleyin.  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   Biçimlendirilmiş yıldız işareti blokları yorumlarla başına değil.  
  
## <a name="program-structure"></a>Program Yapısı  
  
-   Kullanırken `Main` yöntemi, yeni konsol uygulamaları için varsayılan yapıyı kullanın ve kullanmak `My` için komut satırı bağımsız değişkenleri.  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a>Dil Kuralları  
  
### <a name="string-data-type"></a>Dize Veri Türü  
  
-   Dizeleri birleştirmek için bir ve işareti kullanın (&).  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   Döngülere diziler eklemek için kullanın <xref:System.Text.StringBuilder> nesne.  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Olay işleyicileri'ndeki gevşek temsilciler  
 Bağımsız değişkenleri (Object ve EventArgs) açıkça olay işleyicilerine nitelendirmeyin. Bir olaya (örneğin, nesne olarak gönderen, EventArgs olarak e) geçirilen olay bağımsız değişkenlerinin kullanmıyorsanız, gevşek temsilcileri kullanın ve olay bağımsız değişkenlerini kodunuzun içinde bırakın:  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a>İmzasız Veri Türü  
  
-   Kullanım `Integer` gerekli olduğu dışında imzasız türler yerine.  
  
### <a name="arrays"></a>Diziler  
  
-   Bildirim satırında dizileri başlattığınızda kısa sözdizimini kullanın. Örneğin, aşağıdaki sözdizimini kullanın.  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     Aşağıdaki sözdizimini kullanmayın.  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   Dizi göstergesini, tür, değişken üzerinde yerleştirin. Örneğin, aşağıdaki sözdizimini kullanın:  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     Aşağıdaki sözdizimini kullanmayın:  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   Bildirme ve temel veri türleri dizilerini başlatmak {} sözdizimini kullanın. Örneğin, aşağıdaki sözdizimini kullanın:  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     Aşağıdaki sözdizimini kullanmayın:  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a>Kullanım anahtar sözcüğü ile  
 Bir dizi bir nesneye çağrısı yaptığınızda kullanmayı `With` anahtar sözcüğü:  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Try kullan... Catch ve Using deyimlerini özel durum işlemeyi kullandığınızda  
 Kullanmayın `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>IsNot anahtar sözcüğünü kullanın  
 Kullanım `IsNot` anahtar sözcüğü yerine `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>Yeni anahtar sözcüğü  
  
-   Kısa örnekleme kullanın. Örneğin, aşağıdaki sözdizimini kullanın:  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     Önceki satır aşağıdakine eşdeğerdir:  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   Parametresiz oluşturucusu yerine yeni nesneler için nesne başlatıcıları kullanın:  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a>Olay İşleme  
  
-   Kullanım `Handles` yerine `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   Kullanım `AddressOf`ve temsilciyi açıkça örneklemeyin:  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   Bir olay tanımladığınızda kısa sözdizimi kullanın ve derleyicinin temsilciyi tanımlamasına olanak tanır:  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   Bir olay olup olmadığını doğrulamayın `Nothing` (null) çağırmadan önce `RaiseEvent` yöntemi. `RaiseEvent` denetler `Nothing` olayı yükseltmeden önce.  
  
### <a name="using-shared-members"></a>Paylaşılan üyeleri kullanma  
 Çağrı `Shared` bir örnek değişkeninden değil sınıf adını kullanarak üyeleri.  
  
### <a name="use-xml-literals"></a>XML değişmez değerleri kullanma  
 XML değişmez değerleri (örneğin, yük, sorgu ve dönüşüm) XML ile çalışırken karşılaştığınız en yaygın görevleri basitleştirir. XML ile geliştirdiğinizde, aşağıdaki yönergeleri izleyin:  
  
-   XML belgeleri ve XML API'lerini doğrudan çağırmak yerine parçaları oluşturmak için XML sabit değerleri kullanın.  
  
-   XML ad alanları XML sabit değerleri için performans iyileştirmeleri yararlanmak için dosyası veya proje düzeyinde içeri aktarın.  
  
-   Öğeleri ve özniteliklerinin bir XML belgesi erişmek için XML eksen özelliklerini kullanın.  
  
-   Değerler ve gibi API çağrılarını kullanmak yerine var olan değerlerden XML oluşturmak için katıştırılmış ifadeleri kullanın `Add` yöntemi:  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a>LINQ Sorguları  
  
-   Sorgu değişkenleri için anlamlı adlar kullanın:  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   Pascal kullanarak anonim türlerinin özellik adlarının doğru olduğundan emin olmak için bir sorgu içindeki öğeler için adlar sağlamak büyük/küçük harf:  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   Sonuçtaki özellik adları belirsiz olduğunda özellikleri yeniden adlandırın. Sorgunuz bir müşteri adı ve sipariş kimliği verir, örneğin, bunları olarak bırakmak yerine Yeniden Adlandır `Name` ve `ID` sonuç:  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   Sorgu değişkenleri ve aralık değişkenleri bildiriminde tür çıkarımını kullanın:  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   Altında sorgu yan tümcelerini hizalayın `From` deyimi:  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   Kullanım `Where` yan tümceleri önce diğer sorgu yan tümceleri böylece sonraki sorgu yan tümcelerinin filtrelenmiş veri kümesinde çalışır:  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   Kullanım `Join` kullanmak yerine bir birleştirme işlemini açıkça tanımlamak için `Where` örtük olarak bir birleştirme işlemi tanımlamak için:  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli Kodlama Yönergeleri](../../../standard/security/secure-coding-guidelines.md)
