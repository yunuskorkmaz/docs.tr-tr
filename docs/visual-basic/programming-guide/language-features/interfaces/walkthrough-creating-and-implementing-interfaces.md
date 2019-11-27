---
title: Arabirimleri Oluşturma ve Uygulama
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 47176d2e7a512d8e8c27a90ac04d2a2a2af274b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345033"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>İzlenecek yol: Arabirimleri Oluşturma ve Uygulama (Visual Basic)

Arabirimler özellikler, Yöntemler ve olayların özelliklerini ve uygulama ayrıntılarını yapılar veya sınıflar için bir şekilde bırakır.  
  
 Bu izlenecek yol, bir arabirimin nasıl bildirileceğini ve uygulanacağını gösterir.  
  
> [!NOTE]
> Bu izlenecek yol, Kullanıcı arabirimi oluşturma hakkında bilgi sağlamaz.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>Bir arabirim tanımlamak için
  
1. Yeni bir Visual Basic Windows uygulaması projesi açın.  
  
2. **Proje** menüsünde **Modül Ekle** ' ye tıklayarak projeye yeni bir modül ekleyin.  
  
3. Yeni modülü `Module1.vb` adlandırın ve **Ekle**' ye tıklayın. Yeni modülün kodu görüntülenir.  
  
4. `Module` ve `End Module` deyimleri arasında `Interface TestInterface` yazarak ve ardından ENTER ' a basarak `Module1` içinde `TestInterface` adlı bir arabirim tanımlayın. **Kod düzenleyicisi** `Interface` anahtar sözcüğünü girintiler ve bir kod bloğu oluşturmak için bir `End Interface` ifadesini ekler.  
  
5. `Interface` ve `End Interface` deyimleri arasına aşağıdaki kodu yerleştirerek arabirim için bir özellik, yöntem ve olay tanımlayın:  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>Uygulama

 Arabirim üyelerini bildirmek için kullanılan sözdiziminin, sınıf üyelerini bildirmek için kullanılan sözdiziminden farklı olduğunu fark edebilirsiniz. Bu fark, arabirimlerin uygulama kodu içeremeyeceği gerçeğini yansıtır.  
  
### <a name="to-implement-the-interface"></a>Arabirimi uygulamak için
  
1. `Module1`, `End Interface` deyimden sonra, `End Module` ifadesinden önce, sonra ENTER 'a basarak `ImplementationClass` adlı bir sınıf ekleyin.  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     Tümleşik geliştirme ortamı içinde çalışıyorsanız, ENTER tuşuna bastığınızda, **Kod Düzenleyicisi** eşleşen bir `End Class` ifadesini sağlar.  
  
2. Aşağıdaki `Implements` ifadesini, sınıfının uyguladığı arabirimi isimli `ImplementationClass`ekleyin:  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     Bir sınıfın veya yapının üstündeki diğer öğelerden ayrı olarak listelendiğinde, `Implements` ifade, sınıfın veya yapının bir arabirim uyguladığını gösterir.  
  
     Tümleşik geliştirme ortamında çalışıyorsanız, **Kod Düzenleyicisi** , ENTER tuşuna bastığınızda `TestInterface` için gereken sınıf üyelerini uygular ve bir sonraki adımı atlayabilirsiniz.  
  
3. Tümleşik geliştirme ortamında çalışmıyorsanız, `MyInterface`arabirimin tüm üyelerini uygulamanız gerekir. `Event1`, `Method1`ve `Prop1`uygulamak için aşağıdaki kodu `ImplementationClass` ekleyin:  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements` ifade, uygulanan arabirimi ve arabirim üyesini adlandırır.  
  
4. Özellik değerini saklı sınıfa bir özel alan ekleyerek `Prop1` tanımını doldurun:  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     Özellik Al erişimcisindeki `pval` değerini döndürün.  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     Özellik kümesi erişimcisinde `pval` değerini ayarlayın.  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. Aşağıdaki kodu ekleyerek `Method1` tanımını doldurun.  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>Arabirimin uygulamasını test etmek için
  
1. **Çözüm Gezgini**projenizin başlangıç formuna sağ tıklayın ve **kodu görüntüle**' ye tıklayın. Düzenleyici, başlangıç formunuz için sınıfını görüntüler. Varsayılan olarak, başlangıç formu `Form1`olarak adlandırılır.  
  
2. Aşağıdaki `testInstance` alanını `Form1` sınıfına ekleyin:  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     `testInstance` `WithEvents`olarak bildirerek `Form1` sınıfı olaylarını işleyebilir.  
  
3. `testInstance`tarafından oluşturulan olayları işlemek için aşağıdaki olay işleyicisini `Form1` sınıfına ekleyin:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. Uygulama sınıfını test etmek için `Form1` sınıfına `Test` adlı bir altyordam ekleyin:  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     `Test` yordamı, `MyInterface`uygulayan sınıfının bir örneğini oluşturur, bu örneği `testInstance` alanına atar, bir özelliği ayarlar ve arabirim aracılığıyla bir yöntemi çalıştırır.  
  
5. Başlangıç formunuzun `Form1 Load` yordamından `Test` yordamını çağırmak için kod ekleyin:  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. F5 tuşuna basarak `Test` yordamını çalıştırın. "Prop1 9 ' a ayarlanmıştır" iletisi görüntülenir. Tamam ' a tıkladıktan sonra, "Method1 X parametresi 5 olur" iletisi görüntülenir. Tamam ' a tıklayın ve "olay işleyicisi olayı yakalandı" iletisi görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [Arabirimler](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Interface Deyimi](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [Event Deyimi](../../../../visual-basic/language-reference/statements/event-statement.md)
