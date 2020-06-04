---
title: Arabirimleri Oluşturma ve Uygulama
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 89e8f91a04b25b84bc783d5c4f4b91cf12426f72
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405073"
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
  
3. Yeni modülü adlandırın `Module1.vb` ve **Ekle**' ye tıklayın. Yeni modülün kodu görüntülenir.  
  
4. `TestInterface`Ve deyimleri arasına yazarak içinde adlı bir arabirim tanımlayın `Module1` `Interface TestInterface` `Module` `End Module` ve ardından ENTER tuşuna basın. **Kod Düzenleyicisi** , `Interface` anahtar sözcüğünü girintiler ve `End Interface` bir kod bloğu oluşturmak için bir ifade ekler.  
  
5. Aşağıdaki kodu ve deyimleri arasına yerleştirerek arabirim için bir özellik, yöntem ve olay tanımlayın `Interface` `End Interface` :  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>Uygulama

 Arabirim üyelerini bildirmek için kullanılan sözdiziminin, sınıf üyelerini bildirmek için kullanılan sözdiziminden farklı olduğunu fark edebilirsiniz. Bu fark, arabirimlerin uygulama kodu içeremeyeceği gerçeğini yansıtır.  
  
### <a name="to-implement-the-interface"></a>Arabirimi uygulamak için
  
1. `ImplementationClass`Aşağıdaki deyimden `Module1` sonra, ifadesinden sonra, öğesinden önce, sonra `End Interface` `End Module` ENTER tuşuna basarak adlı bir sınıf ekleyin:  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     Tümleşik geliştirme ortamı içinde çalışıyorsanız, ENTER tuşuna bastığınızda, **Kod Düzenleyicisi** eşleşen bir ifade sağlar `End Class` .  
  
2. Aşağıdaki `Implements` ifadesini `ImplementationClass` , sınıfının uyguladığı arabirimi isimsiz olarak ekleyin:  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     Bir sınıfın veya yapının üstündeki diğer öğelerden ayrı olarak listelendiğinde, `Implements` ifade sınıfın veya yapının bir arabirim uyguladığını gösterir.  
  
     Tümleşik geliştirme ortamı içinde çalışıyorsanız, **Kod Düzenleyicisi** , ENTER tuşuna bastığınızda gereken sınıf üyelerini uygular `TestInterface` ve bir sonraki adımı atlayabilirsiniz.  
  
3. Tümleşik geliştirme ortamı içinde çalışmadıysanız, arabirimin tüm üyelerini uygulamanız gerekir `MyInterface` . `ImplementationClass`,, Ve uygulamak için aşağıdaki kodu `Event1` ekleyin `Method1` `Prop1` :  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements`İfade, uygulanan arabirimi ve arabirim üyesini adlandırır.  
  
4. `Prop1`Özellik değerini saklı sınıfa bir özel alan ekleyerek tanımını doldurun:  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     `pval`Özellik Al erişimcisinin öğesinden değerini döndürün.  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     Değerini `pval` özellik kümesi erişimcisinde ayarlayın.  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. `Method1`Aşağıdaki kodu ekleyerek tanımını doldurun.  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>Arabirimin uygulamasını test etmek için
  
1. **Çözüm Gezgini**projenizin başlangıç formuna sağ tıklayın ve **kodu görüntüle**' ye tıklayın. Düzenleyici, başlangıç formunuz için sınıfını görüntüler. Varsayılan olarak, başlangıç formu çağırılır `Form1` .  
  
2. `testInstance`Sınıfına aşağıdaki alanı ekleyin `Form1` :  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     Olarak bildirerek `testInstance` `WithEvents` , `Form1` sınıfı olaylarını işleyebilir.  
  
3. `Form1`Tarafından oluşturulan olayları işlemek için aşağıdaki olay işleyicisini sınıfına ekleyin `testInstance` :  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. `Test` `Form1` Uygulama sınıfını test etmek için sınıfına adlı bir altyordam ekleyin:  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     `Test`Yordam, uygulayan sınıfının bir örneğini oluşturur `MyInterface` , bu örneği alana atar, `testInstance` bir özelliği ayarlar ve arabirim aracılığıyla bir yöntemi çalıştırır.  
  
5. `Test`Başlangıç formunuzun yordamından yordamı çağırmak için kod ekleyin `Form1 Load` :  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. `Test`F5 tuşuna basarak yordamı çalıştırın. "Prop1 9 ' a ayarlanmıştır" iletisi görüntülenir. Tamam ' a tıkladıktan sonra, "Method1 X parametresi 5 olur" iletisi görüntülenir. Tamam ' a tıklayın ve "olay işleyicisi olayı yakalandı" iletisi görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](../../../language-reference/statements/implements-statement.md)
- [Arabirimler](index.md)
- [Interface Deyimi](../../../language-reference/statements/interface-statement.md)
- [Event Deyimi](../../../language-reference/statements/event-statement.md)
