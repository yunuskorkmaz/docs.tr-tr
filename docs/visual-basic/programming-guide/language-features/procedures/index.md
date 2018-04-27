---
title: Visual Basic'de Yordamlar
ms.custom: ''
ms.date: 04/28/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], structured code
- Visual Basic code, procedures
- procedures [Visual Basic], types of
- structured code [Visual Basic], procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 92cb2dd3f356acf89cbe62b5f3f5dc81fce271fc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="procedures-in-visual-basic"></a>Visual Basic'de Yordamlar
A *yordam* bildirimi deyimi tarafından içine Visual Basic deyimleri bloğudur (`Function`, `Sub`, `Operator`, `Get`, `Set`) ve eşleşen bir `End` bildirimi. Visual Basic'te tüm executable deyimleri bazı yordam içinde olmalıdır.  
  
## <a name="calling-a-procedure"></a>Bir yordam çağırma  
 Başka bir yerde kodda bir yordam çağırma. Bu olarak bilinen bir *yordam çağrısı*. Yordam tamamlandığında çalışıyorsa, bu denetimi olarak bilinen, çağrılan kodu döndürür *kodu çağırma*. Çağıran bir deyim veya bir ifade yordamı adıyla belirtir ve denetim aktardığından deyiminde, kodudur.  
  
## <a name="returning-from-a-procedure"></a>Bir yordam döndürme  
 Çalışan tamamlandığında bir yordam çağırma koda denetimini döndürür. Bunu yapmak için onu kullanabilirsiniz bir [dönüş deyimi](../../../../visual-basic/language-reference/statements/return-statement.md), uygun [çıkış deyimi](../../../../visual-basic/language-reference/statements/exit-statement.md) yordamı veya yordam için deyimini [son \<anahtar sözcüğü > deyimi](../../../../visual-basic/language-reference/statements/end-keyword-statement.md)deyimi. Denetim noktası yordam çağrısı aşağıdaki çağıran kodu sonra geçirir.  
  
-   İle bir `Return` deyimi, Denetim döndürür hemen çağıran kodu. Deyimlerini aşağıdaki `Return` deyimi çalıştırmayın. Birden fazla sahip `Return` aynı yordamı deyiminde.  
  
-   İle bir `Exit Sub` veya `Exit Function` deyimi, Denetim döndürür hemen çağıran kodu. Deyimlerini aşağıdaki `Exit` deyimi çalıştırmayın. Birden fazla sahip `Exit` aynı yordamı ve deyiminde karışık `Return` ve `Exit` aynı yordamı deyimlerinde.  
  
-   Bir yordam Hayır varsa `Return` veya `Exit` deyimleri varmadan ile bir `End Sub` veya `End Function`, `End Get`, veya `End Set` yordamı gövdesinin son deyiminden deyimi. `End` Deyimi döndürür denetim hemen çağıran kodu. Yalnızca bir bulunabilir `End` bir yordam deyiminde.  
  
## <a name="parameters-and-arguments"></a>Parametreler ve Bağımsız Değişkenler  
 Çoğu durumda, bir yordam her çağırdığında farklı veri üzerinde çalışması gerekir. Bu bilgiler yordama yordam çağrısı bir parçası olarak geçirebilirsiniz. Sıfır veya daha fazla yordamın tanımlar *parametreleri*, her temsil eden bir değer için geçirmeniz bekler. Yordamı tanımı'ndaki her bir parametreyi karşılık gelen olan bir *bağımsız değişkeni* yordam çağrısında. Bir bağımsız değişkeni için verilen yordam çağrısında karşılık gelen bir parametre geçirin değerini temsil eder.  
  
## <a name="types-of-procedures"></a>Yordamlar türleri  
 Visual Basic çeşitli türlerde yordamlar kullanır:  
  
-   [Alt yordamlar](./sub-procedures.md) eylemleri gerçekleştirme ancak çağıran kodu bir değer döndürmüyor.  
  
-   Olay işleme yordamlar `Sub` oluşumu bir programı veya bir kullanıcı eylemi tarafından gerçekleştirilen bir olaya yanıt olarak execute yordamlar.  
  
-   [İşlev yordamları](./function-procedures.md) çağıran kodu için bir değer döndürür. Döndürmeden önce diğer eylemleri gerçekleştirebilirsiniz.

    C# içinde dönüş yazılan bazı işlevler bir *başvuru dönüş değeri*. İşlev arayanlar dönüş değeri değiştirebilirsiniz ve bu değişikliği adlı nesne durumda yansıtılır. Başvuruya göre bir değer döndüremiyor rağmen Visual Basic 2017 ile başlayarak, başvuru dönüş değerleri, Visual Basic kodu kullanmasını sağlayabilirsiniz. Daha fazla bilgi için bkz: [başvuru dönüş değerleri](ref-return-values.md).
  
-   [Özellik yordamları](./property-procedures.md) dönün ve nesne veya modülleri özelliklerinin değerlerini atayın.  
  
-   [İşleç yordamları](./operator-procedures.md) birini veya her ikisini işlenenler olduğunda yeni tanımlı sınıf veya yapı standart işleci davranışını tanımlayın.  
  
-   [Visual Basic'de genel yordamlar](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) bir veya daha fazla tanımlama *tür parametrelerindeki* çağıran kodu belirli geçirebilirsiniz şekilde normal parametrelerini ek olarak, veri türleri, çağrıda zaman.  
  
## <a name="procedures-and-structured-code"></a>Yordamlar ve yapılandırılmış kod  
 Her uygulamanızda yürütülebilir kod satırı bazı yordam içinde gibi olması gerekir `Main`, `calculate`, veya `Button1_Click`. Büyük yordamları küçük parçalara ayırabilir varsa, daha okunabilir bir uygulamadır.  
  
 Yordamlar, sık kullanılan hesaplamalar, metin ve denetim işleme ve veritabanı işlemleri gibi yinelenen veya paylaşılan görevleri gerçekleştirmek için faydalıdır. Uygulamanız için yapı taşı olarak yordamları kullanabilmeniz için bir yordam, kodunuzda birçok farklı yerlerden çağırabilirsiniz.  
  
 Kodunuzu yordamlarıyla yapılandırılması, aşağıdaki avantajları sunar:  
  
-   Yordamlar, programlarınızı ayrık mantıksal birimler halinde bölün olanak tanır. Yordamlar olmadan programının tamamını ayıklayabilirsiniz çok daha fazla ayrı birimleri kolayca ayıklayabilirsiniz.  
  
-   Bir programda kullanmak için yordamlar geliştirmek sonra diğer programlarla, genellikle az veya hiç değişiklik kullanabilirsiniz. Bu kod yinelemesinden kaçınmak yardımcı olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Yordam Oluşturma](./how-to-create-a-procedure.md)  
 [Alt Yordamlar](./sub-procedures.md)  
 [İşlev Yordamları](./function-procedures.md)  
 [Özellik Yordamları](./property-procedures.md)  
 [İşleç Yordamları](./operator-procedures.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Özyinelemeli Yordamlar](./recursive-procedures.md)  
 [Yordam Aşırı Yüklemesi](./procedure-overloading.md)  
 [Visual Basic'de genel yordamlar](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
