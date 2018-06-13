---
title: Oluşturma ve uygulama arabirimler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: af9305deb60637b642d091501e743f2c7a57ccad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653617"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>İzlenecek yol: Arabirimleri Oluşturma ve Uygulama (Visual Basic)

Arabirimleri özellikleri, yöntemleri ve olay özelliklerini açıklayan, ancak uygulama ayrıntılarını yapıları veya sınıfları kadar bırakın.  
  
 Bu kılavuz, bildirme ve bir arabirim gösterilmiştir.  
  
> [!NOTE]
>  Bu kılavuz, bir kullanıcı arabirimi oluşturma hakkında bilgi sağlamaz.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>Bir arabirimi tanımlamak için
  
1.  Yeni bir Visual Basic Windows uygulama projesi açın.  
  
2.  Yeni bir modül projeye tıklayarak ekleyin **Modül Ekle** üzerinde **proje** menüsü.  
  
3.  Yeni modül adı `Module1.vb` tıklatıp **Ekle**. Yeni modül kodu görüntülenir.  
  
4.  Adlı bir arabirim tanımlayın `TestInterface` içinde `Module1` yazarak `Interface TestInterface` arasında `Module` ve `End Module` deyimleri ve sonra ENTER tuşuna basın. **Kod düzenleyicisinde** girintileri `Interface` anahtar sözcüğü ve ekleyen bir `End Interface` kod bloğu oluşturmak için ifade.  
  
5.  Aşağıdaki kod arasında koyarak özelliği, yöntemi ve olay arabirimi tanımlamak `Interface` ve `End Interface` deyimleri:  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>Uygulama

 Arabirim üyeleri bildirmek için kullanılan sözdizimi sınıf üyesi bildirmek için kullanılan sözdiziminden, farklı olduğunu fark edebilirsiniz. Bu farkı arabirimler uygulama kodu içeremez olgu yansıtır.  
  
### <a name="to-implement-the-interface"></a>Arabirim uygulamak için
  
1.  Adlı bir sınıf ekleyin `ImplementationClass` şu deyimi ekleyerek `Module1`, sonra `End Interface` deyimi önce `End Module` deyimi ve sonra ENTER tuşuna basın:  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     Tümleşik geliştirme ortamında çalışıyorsanız **Kod Düzenleyicisi** eşleşen bir sağlayan `End Class` deyimi ENTER tuşuna basın.  
  
2.  Aşağıdakileri ekleyin `Implements` ifadesine `ImplementationClass`, hangi arabirimi sınıfı adları uygular:  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     Bir sınıf veya yapı, üstündeki diğer öğelerden ayrı olarak listelenen `Implements` deyimi gösteren sınıf veya yapı bir arabirimi uygular.  
  
     Tümleşik geliştirme ortamında çalışıyorsanız **Kod düzenleyicisinde** gerektirdiği sınıf üyeleri uygulayan `TestInterface` zaman ENTER tuşuna basın ve sonraki adıma atlayabilirsiniz.  
  
3.  Tümleşik geliştirme ortamında çalışmıyorsanız arabirimi tüm üyeleri uygulamalıdır `MyInterface`. Aşağıdaki kodu ekleyin `ImplementationClass` uygulamak için `Event1`, `Method1`, ve `Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements` Deyimi adları uygulanan arabirim üyesini ve arabirim.  
  
4.  Tanımını tamamlamak `Prop1` özellik değeri depolanan sınıfı için özel bir alan ekleyerek:  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     Değeri döndürmesi `pval` özelliğinden get erişimcisi.  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     Değerini `pval` özelliğinde ayarlama erişimcisi.  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5.  Tanımını tamamlamak `Method1` aşağıdaki kodu ekleyerek düzenleyin.  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>Arabirim uygulanmasını test etmek için
  
1.  Projenizde başlangıç formu sağ **Çözüm Gezgini**, tıklatıp **görünümü kodu**. Düzenleyici başlangıç formunuz için sınıf görüntüler. Varsayılan olarak, başlangıç formu adlı `Form1`.  
  
2.  Aşağıdakileri ekleyin `testInstance` alanı `Form1` sınıfı:  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     Bildirme tarafından `testInstance` olarak `WithEvents`, `Form1` sınıfı olaylarına işleyebilir.  
  
3.  Aşağıdaki olay işleyicisi ekleme `Form1` tarafından başlatılan olayları işlemek için sınıf `testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4.  Adlı bir alt yordama ekleme `Test` için `Form1` sınıfı uygulama sınıfı test etmek için:  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     `Test` Yordam uygulayan sınıf örneği oluşturur `MyInterface`, bu örneğe atar `testInstance` alan, bir özelliği ayarlar ve bir yöntem arabirimi aracılığıyla çalıştırır.  
  
5.  Çağırmak için kodu ekleyin `Test` yordamdan `Form1 Load` başlangıç formu yordam:  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6.  Çalıştırma `Test` F5'e basarak yordamı. İleti "Prop1 9 ayarlandı" görüntülenir. "X parametresi Method1 için 5." iletisi Tamam ' ı sonra görüntülenir. Tamam'ı tıklatın ve "olay olay işleyicisi yakalanan" iletisi görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

 [Implements Deyimi](../../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Arabirimler](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [Interface Deyimi](../../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Event Deyimi](../../../../visual-basic/language-reference/statements/event-statement.md)  