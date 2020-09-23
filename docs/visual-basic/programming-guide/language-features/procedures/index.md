---
title: Yordamlar
ms.date: 04/28/2017
helpviewer_keywords:
- procedures [Visual Basic], structured code
- Visual Basic code, procedures
- procedures [Visual Basic], types of
- structured code [Visual Basic], procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
ms.openlocfilehash: 926d2dcc7f29102457d5ed9632e7455f8f0c7b96
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071332"
---
# <a name="procedures-in-visual-basic"></a>Visual Basic'de Yordamlar

*Yordam* , bir bildirim deyimi ( `Function` ,, `Sub` `Operator` , `Get` , `Set` ) ve eşleşen `End` bildirim tarafından alınan Visual Basic deyimlerinin bir bloğudur. Visual Basic tüm çalıştırılabilir deyimler bazı yordamda olmalıdır.  
  
## <a name="calling-a-procedure"></a>Yordam çağırma  

 Koddaki başka bir yerden yordam çağırılır. Bu, *yordam çağrısı*olarak bilinir. Yordam çalışmayı bitirdiğinde, *çağıran*kod olarak bilinen, çağrılan koda denetim döndürür. Çağıran kod, bir deyim veya deyim içindeki bir ifadedir ve bu yordam ada göre yordamı belirtir ve denetimi buna aktarır.  
  
## <a name="returning-from-a-procedure"></a>Bir yordamdan dönme  

 Yordam, çalışmayı tamamladığında çağıran koda denetim döndürür. Bunu yapmak için, yordam için bir [return ifadesini](../../../language-reference/statements/return-statement.md), uygun [Exit bildiri](../../../language-reference/statements/exit-statement.md) ifadesini veya yordamın [End \<keyword> deyimi](../../../language-reference/statements/end-keyword-statement.md) ifadesini kullanabilirsiniz. Daha sonra Denetim, yordam çağrısının noktasını izleyen çağırma koduna geçer.  
  
- Bir `Return` ifadesiyle denetim, çağırma koduna hemen geri döner. `Return`Deyimden sonraki deyimler çalıştırılmaz. Aynı yordamda birden fazla deyime sahip olabilirsiniz `Return` .  
  
- `Exit Sub`Or `Exit Function` ifadesiyle denetim, çağırma koduna hemen geri döner. `Exit`Deyimden sonraki deyimler çalıştırılmaz. Aynı yordamda birden fazla deyime sahip olabilirsiniz `Exit` ve `Return` `Exit` aynı yordamda ve deyimlerini karıştırabilirsiniz.  
  
- Bir yordamda `Return` veya deyimleri yoksa, `Exit` `End Sub` `End Function` `End Get` `End Set` yordam gövdesinin son deyiminden sonra bir veya, ya da ifadesiyle sonlanır. `End`İfade, çağırma koduna anında denetim döndürür. Yordamda yalnızca bir `End` deyiminiz olabilir.  
  
## <a name="parameters-and-arguments"></a>Parametreler ve Bağımsız Değişkenler  

 Çoğu durumda, bir yordamın her çağırdığınızda farklı veriler üzerinde çalışması gerekir. Yordam çağrısının bir parçası olarak bu bilgileri yordama geçirebilirsiniz. Yordam sıfır veya daha fazla *parametreyi*tanımlar, her biri, kendisine geçirilmesini bekleyen bir değeri temsil eder. Yordam tanımındaki her parametreye karşılık gelen yordam çağrısındaki bir *bağımsız değişkendir* . Bağımsız değişken, belirli bir yordam çağrısında karşılık gelen parametreye geçirdiğiniz değeri temsil eder.  
  
## <a name="types-of-procedures"></a>Yordam türleri  

 Visual Basic çeşitli yordam türlerini kullanır:  
  
- [Alt yordamlar](./sub-procedures.md) eylemleri gerçekleştirir, ancak çağırma koduna bir değer döndürmez.  
  
- Olay işleme yordamları, `Sub` Kullanıcı eylemine göre veya bir programdaki bir oluşum tarafından oluşturulan bir olaya yanıt olarak yürütülen yordamlardır.  
  
- [Işlev yordamları](./function-procedures.md) , çağırma koduna bir değer döndürür. Bu işlemler, döndürmeden önce başka eylemler gerçekleştirebilir.

    C# dilinde yazılan bazı işlevler bir *Başvuru dönüş değeri*döndürür. İşlev çağıranları dönüş değerini değiştirebilir ve bu değişiklik çağrılan nesnenin durumunda yansıtılır. Visual Basic 2017 ' den başlayarak, Visual Basic kodu başvuru dönüş değerlerini tüketebilir, ancak başvuruya göre bir değer döndüremez. Daha fazla bilgi için bkz. [Başvuru dönüş değerleri](ref-return-values.md).
  
- [Özellik yordamları](./property-procedures.md) , nesne veya modüllerde özelliklerin değerlerini döndürür ve atar.  
  
- [Işleç yordamları](./operator-procedures.md) , işlenenleri bir veya her ikisi de yeni tanımlanmış bir sınıf veya yapı olduğunda standart işlecin davranışını tanımlar.  
  
- [Visual Basic genel yordamları](../data-types/generic-procedures.md) normal parametrelerine ek olarak bir veya daha fazla *tür parametresi* tanımlar, bu nedenle çağıran kod her bir çağrı yaptığında belirli veri türlerini geçirebilir.  
  
## <a name="procedures-and-structured-code"></a>Yordamlar ve yapılandırılmış kod  

 Uygulamanızdaki her çalıştırılabilir kod satırının,, veya gibi bir yordamın içinde olması gerekir `Main` `calculate` `Button1_Click` . Büyük yordamları daha küçük olanlara bölüyorsanız, uygulamanız daha okunabilir olur.  
  
 Yordamlar, sık kullanılan hesaplamalar, metin ve denetim işleme ve veritabanı işlemleri gibi yinelenen veya paylaşılan görevler gerçekleştirmek için yararlıdır. Kodunuzda birçok farklı yerden bir yordam çağırabilirsiniz, böylece yordamları uygulamanızın yapı taşları olarak kullanabilirsiniz.  
  
 Kodunuzu yordamlar ile yapılandırmak aşağıdaki avantajları sağlar:  
  
- Yordamlar, programlarınızı ayrı mantıksal birimlere bölmek için izin verir. Bir programın tümünde yordamlar olmadan Hata ayıklayabilmeniz için ayrı birimlerde daha kolay hata ayıklaması yapabilirsiniz.  
  
- Bir programda kullanım için prosedürleri geliştirdikten sonra, bunları diğer programlarda (çoğunlukla çok az değişiklik yapmadan) kullanabilirsiniz. Bu, kod tekrardan kaçınmanıza yardımcı olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Yordam Oluşturma](./how-to-create-a-procedure.md)
- [Alt Yordamlar](./sub-procedures.md)
- [İşlev Yordamları](./function-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Özyinelemeli Yordamlar](./recursive-procedures.md)
- [Yordam Aşırı Yüklemesi](./procedure-overloading.md)
- [Visual Basic'de Genel Yordamlar](../data-types/generic-procedures.md)
- [Nesneler ve sınıflar](../objects-and-classes/index.md)
