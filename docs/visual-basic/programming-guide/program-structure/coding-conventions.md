---
title: Visual Basic Kodlama Kuralları
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: f73648888b28c349104a70e78c29eb208d438b78
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814568"
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
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
-   Biçimlendirilmiş yıldız işareti blokları yorumlarla başına değil.  
  
## <a name="program-structure"></a>Program Yapısı  
  
-   Kullanırken `Main` yöntemi, yeni konsol uygulamaları için varsayılan yapıyı kullanın ve kullanmak `My` için komut satırı bağımsız değişkenleri.  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a>Dil Kuralları  
  
### <a name="string-data-type"></a>Dize Veri Türü  
  
-   Dizeleri birleştirmek için bir ve işareti kullanın (&).  
  
     [!code-vb[VbVbalrGuidelines#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#4)]  
  
-   Döngülere diziler eklemek için kullanın <xref:System.Text.StringBuilder> nesne.  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Olay işleyicileri'ndeki gevşek temsilciler  
 Bağımsız değişkenleri (Object ve EventArgs) açıkça olay işleyicilerine nitelendirmeyin. Bir olaya (örneğin, nesne olarak gönderen, EventArgs olarak e) geçirilen olay bağımsız değişkenlerinin kullanmıyorsanız, gevşek temsilcileri kullanın ve olay bağımsız değişkenlerini kodunuzun içinde bırakın:  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a>İmzasız Veri Türü  
  
-   Kullanım `Integer` gerekli olduğu dışında imzasız türler yerine.  
  
### <a name="arrays"></a>Diziler  
  
-   Bildirim satırında dizileri başlattığınızda kısa sözdizimini kullanın. Örneğin, aşağıdaki sözdizimini kullanın.  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     Aşağıdaki sözdizimini kullanmayın.  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
-   Dizi göstergesini, tür, değişken üzerinde yerleştirin. Örneğin, aşağıdaki sözdizimini kullanın:  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     Aşağıdaki sözdizimini kullanmayın:  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
-   Bildirme ve temel veri türleri dizilerini başlatmak {} sözdizimini kullanın. Örneğin, aşağıdaki sözdizimini kullanın:  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     Aşağıdaki sözdizimini kullanmayın:  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a>Kullanım anahtar sözcüğü ile  
 Bir dizi bir nesneye çağrısı yaptığınızda kullanmayı `With` anahtar sözcüğü:  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Try kullan... Catch ve Using deyimlerini özel durum işlemeyi kullandığınızda  
 Kullanmayın `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>IsNot anahtar sözcüğünü kullanın  
 Kullanım `IsNot` anahtar sözcüğü yerine `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>Yeni anahtar sözcüğü  
  
-   Kısa örnekleme kullanın. Örneğin, aşağıdaki sözdizimini kullanın:  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     Önceki satır aşağıdakine eşdeğerdir:  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
-   Parametresiz oluşturucusu yerine yeni nesneler için nesne başlatıcıları kullanın:  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a>Olay İşleme  
  
-   Kullanım `Handles` yerine `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
-   Kullanım `AddressOf`ve temsilciyi açıkça örneklemeyin:  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
-   Bir olay tanımladığınızda kısa sözdizimi kullanın ve derleyicinin temsilciyi tanımlamasına olanak tanır:  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
-   Bir olay olup olmadığını doğrulamayın `Nothing` (null) çağırmadan önce `RaiseEvent` yöntemi. `RaiseEvent` denetler `Nothing` olayı yükseltmeden önce.  
  
### <a name="using-shared-members"></a>Paylaşılan üyeleri kullanma  
 Çağrı `Shared` bir örnek değişkeninden değil sınıf adını kullanarak üyeleri.  
  
### <a name="use-xml-literals"></a>XML değişmez değerleri kullanma  
 XML değişmez değerleri (örneğin, yük, sorgu ve dönüşüm) XML ile çalışırken karşılaştığınız en yaygın görevleri basitleştirir. XML ile geliştirdiğinizde, aşağıdaki yönergeleri izleyin:  
  
-   XML belgeleri ve XML API'lerini doğrudan çağırmak yerine parçaları oluşturmak için XML sabit değerleri kullanın.  
  
-   XML ad alanları XML sabit değerleri için performans iyileştirmeleri yararlanmak için dosyası veya proje düzeyinde içeri aktarın.  
  
-   Öğeleri ve özniteliklerinin bir XML belgesi erişmek için XML eksen özelliklerini kullanın.  
  
-   Değerler ve gibi API çağrılarını kullanmak yerine var olan değerlerden XML oluşturmak için katıştırılmış ifadeleri kullanın `Add` yöntemi:  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a>LINQ Sorguları  
  
-   Sorgu değişkenleri için anlamlı adlar kullanın:  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
-   Pascal kullanarak anonim türlerinin özellik adlarının doğru olduğundan emin olmak için bir sorgu içindeki öğeler için adlar sağlamak büyük/küçük harf:  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
-   Sonuçtaki özellik adları belirsiz olduğunda özellikleri yeniden adlandırın. Sorgunuz bir müşteri adı ve sipariş kimliği verir, örneğin, bunları olarak bırakmak yerine Yeniden Adlandır `Name` ve `ID` sonuç:  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
-   Sorgu değişkenleri ve aralık değişkenleri bildiriminde tür çıkarımını kullanın:  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
-   Altında sorgu yan tümcelerini hizalayın `From` deyimi:  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
-   Kullanım `Where` yan tümceleri önce diğer sorgu yan tümceleri böylece sonraki sorgu yan tümcelerinin filtrelenmiş veri kümesinde çalışır:  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
-   Kullanım `Join` kullanmak yerine bir birleştirme işlemini açıkça tanımlamak için `Where` örtük olarak bir birleştirme işlemi tanımlamak için:  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../standard/security/secure-coding-guidelines.md)
