---
title: Oluşturma ve uygulama arabirimler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: faed4d3c9498938e022daf821dd0aefbcbcf2e8d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322036"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>İzlenecek yol: Oluşturma ve uygulama arabirimler (Visual Basic)

Arabirimler, özellikleri, yöntemleri ve olayları özelliklerini açıklayan, ancak yapıların veya sınıfların kadar uygulama ayrıntılarını bırakın.  
  
 Bu izlenecek yol, bildirme ve bir arabirim gösterilmektedir.  
  
> [!NOTE]
>  Bu izlenecek yol, bir kullanıcı arabirimi oluşturma hakkında bilgi sağlamaz.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>Arabirim tanımlamak için
  
1. Yeni bir Visual Basic Windows uygulaması projesi açın.  
  
2. Yeni modül tıklayarak projeye ekleyin. **Modül Ekle** üzerinde **proje** menüsü.  
  
3. Yeni modül adı `Module1.vb` tıklatıp **Ekle**. Yeni modül kodu görüntülenir.  
  
4. Adlı bir arabirim tanımla `TestInterface` içinde `Module1` yazarak `Interface TestInterface` arasında `Module` ve `End Module` deyimleri ve sonra ENTER tuşuna basın. **Kod Düzenleyicisi** girintileri `Interface` anahtar sözcüğü ve ekler bir `End Interface` deyimini bir kod bloğu oluşturur.  
  
5. Bir özellik, yöntemi ve olay arabirimi için arasına aşağıdaki kodu yerleştirerek tanımlamak `Interface` ve `End Interface` ifadeleri:  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>Uygulama

 Arabirim üyeleri bildirmek için kullanılan sözdizimi sınıf üyeleri bildirmek için kullanılan söz dizimi farklı olduğunu fark edebilirsiniz. Bu fark, arabirimler uygulama kodu içeremez olgu yansıtır.  
  
### <a name="to-implement-the-interface"></a>Arabirim uygulamak için
  
1. Adlı bir sınıf ekleyin `ImplementationClass` şu deyimi ekleyerek `Module1`, sonra `End Interface` deyimi önce `End Module` deyimi ve sonra ENTER tuşuna basın:  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     Tümleşik geliştirme ortamında çalışıyorsanız **Kod Düzenleyicisi** eşleşen sağlayan `End Class` deyimi ENTER tuşuna basın.  
  
2. Aşağıdaki `Implements` ifadesine `ImplementationClass`, sınıf, arabirim adları uygular:  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     Bir sınıf veya yapı, üst kısmındaki diğer öğelerden ayrı olarak listelenen `Implements` deyimi, sınıfın veya yapının bir arabirim uyguladığını belirtir.  
  
     Tümleşik geliştirme ortamında çalışıyorsanız **Kod Düzenleyicisi** uygulayan sınıf üyelerini gerektirdiği `TestInterface` olduğunda ENTER tuşuna basın ve sonraki adıma atlayabilirsiniz.  
  
3. Tümleşik geliştirme ortamında çalışmıyorsanız, arabirimin tüm üyelerini uygulamalıdır `MyInterface`. Aşağıdaki kodu ekleyin `ImplementationClass` uygulamak için `Event1`, `Method1`, ve `Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements` Arabirimi ve uygulanan arabirim üyesi bildirimi adları.  
  
4. Tanımını tamamlamak `Prop1` özellik değeri depolanan sınıfı için özel bir alan ekleyerek:  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     Dönüş değeri `pval` erişimci özelliğin alın.  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     Değerini `pval` erişimci özelliğini ayarlayın.  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. Tanımını tamamlamak `Method1` aşağıdaki kodu ekleyerek.  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>Arabirim uygulamasını test etmek için
  
1. Başlangıç formu için projenizde sağ **Çözüm Gezgini**, tıklatıp **kodu görüntüle**. Düzenleyici, başlangıç formu için sınıf görüntüler. Varsayılan olarak, başlangıç formu çağrılır `Form1`.  
  
2. Aşağıdaki `testInstance` alanı `Form1` sınıfı:  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     Bildirmek `testInstance` olarak `WithEvents`, `Form1` sınıf olayları işleyebilir.  
  
3. Eklemek için aşağıdaki olay işleyicisini `Form1` tarafından başlatılan olayları işlemek için sınıfın `testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. Adlı bir alt yordam Ekle `Test` için `Form1` uygulama sınıfımızın test edilecek sınıf:  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     `Test` Yordamı uygulayan sınıfın bir örneğini oluşturur `MyInterface`, bu örneğe atar `testInstance` alan, bir özelliğini ayarlar ve bir yöntem arabirimi aracılığıyla çalıştırır.  
  
5. Çağırmak için kod ekleyin `Test` yordamdan `Form1 Load` başlangıç formunuzun yordam:  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. Çalıştırma `Test` F5 tuşuna basarak yordamı. İleti "Prop1 9'a ayarlanmış" görüntülenir. Tamam, "X parametresi Method1 için 5'tir" iletisi tıkladıktan sonra görüntülenir. Tamam'ı tıklatın ve "olay işleyicisi, olay yakalandı" iletisi görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [Arabirimler](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Interface Deyimi](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [Event Deyimi](../../../../visual-basic/language-reference/statements/event-statement.md)
