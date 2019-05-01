---
title: Visual Basic'de Yordamlar
ms.date: 04/28/2017
helpviewer_keywords:
- procedures [Visual Basic], structured code
- Visual Basic code, procedures
- procedures [Visual Basic], types of
- structured code [Visual Basic], procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
ms.openlocfilehash: dfd366cd823931962af878de59225ea183fff7c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863512"
---
# <a name="procedures-in-visual-basic"></a>Visual Basic'de Yordamlar
A *yordamı* Visual Basic deyimleri tarafından bir bildirim deyiminin içine bloğudur (`Function`, `Sub`, `Operator`, `Get`, `Set`) ile eşleşen bir `End` bildirimi. Visual Basic'te tüm yürütülebilir deyimleri bazı yordam içinde olmalıdır.  
  
## <a name="calling-a-procedure"></a>Bir yordamı çağırma  
 Başka bir yerde kodda bir yordam çağırma. Bu olarak bilinen bir *yordam çağrısı*. Yordam tamamlandığında çalışan, denetimi olarak da bilinen, çağrılan kodu üretebiliyorsa *kodu çağırma*. Çağıran bir deyim ya da yordamın adını belirtir ve denetim için aktarımları bir deyimi içindeki bir ifadenin kodudur.  
  
## <a name="returning-from-a-procedure"></a>Döndüren bir yordam  
 Bir yordam, çalışması tamamlandığında çağrıldığı koda denetimini döndürür. Bunu yapmak için bunu kullanabilirsiniz bir [dönüş deyimi](../../../../visual-basic/language-reference/statements/return-statement.md), uygun [çıkış bildirimi](../../../../visual-basic/language-reference/statements/exit-statement.md) yordamı veya yordam bildirimi [son \<anahtar sözcüğü > deyimi](../../../../visual-basic/language-reference/statements/end-keyword-statement.md)deyimi. Denetim noktasını yordam çağrısının çağrıldığı koda ardından geçer.  
  
- İle bir `Return` deyimi, denetimi döndürür hemen çağrıldığı koda. Deyimlerini aşağıdaki `Return` deyimi çalıştırmayın. Birden fazla aboneliğiniz `Return` aynı yordamındaki.  
  
- İle bir `Exit Sub` veya `Exit Function` deyimi, denetimi döndürür hemen çağrıldığı koda. Deyimlerini aşağıdaki `Exit` deyimi çalıştırmayın. Birden fazla aboneliğiniz `Exit` aynı yordamı ve deyiminde karıştırmak `Return` ve `Exit` deyimleri aynı yordam içinde.  
  
- Bir yordam varsa `Return` veya `Exit` deyimleri varmadan ile bir `End Sub` veya `End Function`, `End Get`, veya `End Set` son deyim yordamı gövdesi aşağıdaki deyimi. `End` Deyimi döndürür denetimi hemen çağrıldığı koda. Tek sahip `End` bir yordamındaki.  
  
## <a name="parameters-and-arguments"></a>Parametreler ve Bağımsız Değişkenler  
 Çoğu durumda, bir yordam her çağırdığında farklı veri çalışması gerekiyor. Bu bilgiler, bir yordama yordam çağrısı bir parçası olarak geçirebilirsiniz. Sıfır veya daha fazla yordamın tanımlar *parametreleri*, her temsil eden bir değer geçirin için bekler. Yordam tanımındaki her parametresine karşılık gelen olduğu bir *bağımsız değişken* yordam çağrısında. Bağımsız değişken, belirli bir yordamı çağrıda karşılık gelen parametresine geçirdiğiniz değerini temsil eder.  
  
## <a name="types-of-procedures"></a>Yordamları türleri  
 Visual Basic çeşitli türlerde yordamlar kullanır:  
  
- [Alt yordamlar](./sub-procedures.md) Eylemler gerçekleştirir ancak çağrıldığı koda bir değer döndürmüyor.  
  
- Olay işleme yordamlar `Sub` kullanıcı eylemi veya bir programda bir örneği tarafından oluşturulan bir olaya yanıt olarak yürütülen yordamları.  
  
- [İşlev yordamları](./function-procedures.md) çağrıldığı koda bir değer döndürür. Sonuç döndürülmeden önce diğer eylemleri gerçekleştirebilirsiniz.

    Bazı işlevler yazılan C# dönüş bir *başvuru dönüş değeri*. Çağıranlar işlevi dönüş değeri değiştirebilirsiniz ve bu değişiklik çağrılan nesnenin durumunda yansıtılır. Visual Basic 2017'den itibaren bir değer başvuru ile döndürülemez olsa da Visual Basic kodunu başvuru dönüş değerleri kullanabilir. Daha fazla bilgi için [başvuru dönüş değerleri](ref-return-values.md).
  
- [Özellik yordamları](./property-procedures.md) dönün ve nesne veya modülleri özelliklerinin değerlerini atayın.  
  
- [İşleç yordamları](./operator-procedures.md) birini veya her ikisini işlenenler olduğunda, bir yeni tanımlı sınıf veya yapı standart işlecinin davranışını tanımlayın.  
  
- [Visual Basic'de genel yordamlar](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) bir veya daha fazla tanımlama *tür parametrelerindeki* çağıran kod belirli geçirebilirsiniz. böylece normal parametrelerinin yanı sıra veri türleri bu çağrıda saat.  
  
## <a name="procedures-and-structured-code"></a>Yordamlar ve yapılandırılmış kod  
 Her uygulamanızdaki yürütülebilir kod satırı gibi bazı yordam içinde olmalıdır `Main`, `calculate`, veya `Button1_Click`. Büyük yordamları küçük parçalara ayırabilir, uygulamanızı daha okunabilir olur.  
  
 Yordamları, sık kullanılan hesaplama, metin ve denetim ve veritabanı işlemleri gibi yinelenen veya paylaşılan görevleri gerçekleştirmek için faydalıdır. Uygulamanız için yapı taşı olarak yordamları kullanabilmeniz için kodunuza, pek çok farklı yerden bir yordam çağırabilir.  
  
 Kodunuzu yordamları ile yapılandırılması size aşağıdaki avantajları sunar:  
  
- Yordamları programlarınızın ayrı mantıksal birimler halinde bölmek sağlar. Programın tamamındaki yordamları olmadan hata ayıklama çok daha fazla ayrı birimleri kolayca hata ayıklaması yapabilirsiniz.  
  
- Bir programda kullanmak için yordamlar geliştirmek sonra diğer programlara, genellikle çok az kayıpla veya hiç değişiklik kullanabilirsiniz. Kod yinelemesinden kaçınmak yardımcı olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Bir yordam oluşturma](./how-to-create-a-procedure.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Özyinelemeli Yordamlar](./recursive-procedures.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Visual Basic'de genel yordamlar](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
