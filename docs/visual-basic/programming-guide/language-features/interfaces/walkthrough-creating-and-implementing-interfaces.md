---
title: Arabirimleri oluşturma ve uygulama (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 62e301e9eb366d14b58088d3e2cda3b567d17f5b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923314"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>İzlenecek yol: Arabirimleri oluşturma ve uygulama (Visual Basic)

Arabirimler özellikler, Yöntemler ve olayların özelliklerini ve uygulama ayrıntılarını yapılar veya sınıflar için bir şekilde bırakır.  
  
 Bu izlenecek yol, bir arabirimin nasıl bildirileceğini ve uygulanacağını gösterir.  
  
> [!NOTE]
> Bu izlenecek yol, Kullanıcı arabirimi oluşturma hakkında bilgi sağlamaz.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>Bir arabirim tanımlamak için
  
1. Yeni bir Visual Basic Windows uygulaması projesi açın.  
  
2. **Proje** menüsünde **Modül Ekle** ' ye tıklayarak projeye yeni bir modül ekleyin.  
  
3. Yeni modülü `Module1.vb` adlandırın ve **Ekle**' ye tıklayın. Yeni modülün kodu görüntülenir.  
  
4. `TestInterface` `Module1` Ve deyimleriarasına`Interface TestInterface` yazarak içinde adlı bir arabirim tanımlayın ve ardından ENTER tuşuna basın. `End Module` `Module` **Kod Düzenleyicisi** , `Interface` anahtar sözcüğünü girintiler ve bir kod `End Interface` bloğu oluşturmak için bir ifade ekler.  
  
5. Aşağıdaki kodu `Interface` ve `End Interface` deyimleri arasına yerleştirerek arabirim için bir özellik, yöntem ve olay tanımlayın:  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>Uygulama

 Arabirim üyelerini bildirmek için kullanılan sözdiziminin, sınıf üyelerini bildirmek için kullanılan sözdiziminden farklı olduğunu fark edebilirsiniz. Bu fark, arabirimlerin uygulama kodu içeremeyeceği gerçeğini yansıtır.  
  
### <a name="to-implement-the-interface"></a>Arabirimi uygulamak için
  
1. Aşağıdaki `ImplementationClass` `End Interface` `End Module` deyimden sonra ,ifadesindensonra,öğesindenönce,sonraENTERtuşunabasarakadlıbirsınıfekleyin:`Module1`  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     Tümleşik geliştirme ortamı içinde çalışıyorsanız, ENTER tuşuna bastığınızda, **Kod Düzenleyicisi** eşleşen `End Class` bir ifade sağlar.  
  
2. Aşağıdaki `Implements` ifadesini, sınıfının uyguladığı `ImplementationClass`arabirimi isimsiz olarak ekleyin:  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     Bir sınıfın veya yapının üstündeki diğer öğelerden ayrı olarak listelendiğinde, `Implements` ifade sınıfın veya yapının bir arabirim uyguladığını gösterir.  
  
     Tümleşik geliştirme ortamı içinde çalışıyorsanız, **Kod Düzenleyicisi** , ENTER tuşuna bastığınızda gereken `TestInterface` sınıf üyelerini uygular ve bir sonraki adımı atlayabilirsiniz.  
  
3. Tümleşik geliştirme ortamı içinde çalışmadıysanız, arabirimin `MyInterface`tüm üyelerini uygulamanız gerekir. `ImplementationClass` `Event1`, ,Ve`Prop1`uygulamak için aşağıdaki kodu ekleyin: `Method1`  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements` İfade, uygulanan arabirimi ve arabirim üyesini adlandırır.  
  
4. Özellik değerini saklı sınıfa `Prop1` bir özel alan ekleyerek tanımını doldurun:  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     Özellik Al erişimcisinin `pval` öğesinden değerini döndürün.  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     Değerini `pval` özellik kümesi erişimcisinde ayarlayın.  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. Aşağıdaki kodu ekleyerek tanımını `Method1` doldurun.  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>Arabirimin uygulamasını test etmek için
  
1. **Çözüm Gezgini**projenizin başlangıç formuna sağ tıklayın ve **kodu görüntüle**' ye tıklayın. Düzenleyici, başlangıç formunuz için sınıfını görüntüler. Varsayılan olarak, başlangıç formu çağırılır `Form1`.  
  
2. `Form1` Sınıfına aşağıdaki `testInstance` alanı ekleyin:  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     Olarak `testInstance` bildirerek`WithEvents`, sınıfı`Form1` olaylarını işleyebilir.  
  
3. `Form1` Tarafından`testInstance`oluşturulan olayları işlemek için aşağıdaki olay işleyicisini sınıfına ekleyin:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. Uygulama sınıfını test etmek `Test` için `Form1` sınıfına adlı bir altyordam ekleyin:  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     Yordam, uygulayan `MyInterface`sınıfının bir örneğini oluşturur, bu örneği `testInstance` alana atar, bir özelliği ayarlar ve arabirim aracılığıyla bir yöntemi çalıştırır. `Test`  
  
5. Başlangıç formunuzun `Test` `Form1 Load` yordamından yordamı çağırmak için kod ekleyin:  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. F5 tuşuna basarak yordamı çalıştırın. `Test` "Prop1 9 ' a ayarlanmıştır" iletisi görüntülenir. Tamam ' a tıkladıktan sonra, "Method1 X parametresi 5 olur" iletisi görüntülenir. Tamam ' a tıklayın ve "olay işleyicisi olayı yakalandı" iletisi görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [Arabirimler](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Interface Deyimi](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [Event Deyimi](../../../../visual-basic/language-reference/statements/event-statement.md)
