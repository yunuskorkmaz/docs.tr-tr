---
title: 'İzlenecek yol: (Visual Basic) COM nesnelerinde kalıtım uygulama'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: d3814dddb0e39bf986e8d6ee88b3c7b4ec759748
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980457"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>İzlenecek yol: (Visual Basic) COM nesnelerinde kalıtım uygulama
Visual Basic sınıfları türetebilirsiniz `Public` olanlar Visual Basic'in önceki sürümlerinde oluşturulan COM nesnelerini sınıfları. Özellikler ve yöntemler COM nesnelerden devralınan sınıf geçersiz kılınan gibi özellikleri olarak aşırı ve herhangi bir taban sınıf yöntemlerini geçersiz kılınmış veya aşırı yüklenmiş. COM nesneleri içinden devralma derlemeniz istemediğiniz var olan bir sınıf kitaplığı olduğunda yararlıdır.  
  
 Aşağıdaki yordam Visual Basic 6.0 bir sınıf içeren bir COM nesnesi oluşturur ve ardından bir temel sınıf olarak kullanmak nasıl gösterir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>Bu kılavuzda kullanılan COM nesnesi oluşturmak için  
  
1.  Visual Basic 6. 0'da, yeni bir ActiveX DLL projesi açın. Adlı bir proje `Project1` oluşturulur. Adlı bir sınıf sahip `Class1`.  
  
2.  İçinde **Proje Gezgini**, sağ **Project1**ve ardından **Project1 özellikleri**. **Proje özellikleri** iletişim kutusu görüntülenir.  
  
3.  Üzerinde **genel** sekmesinde **proje özellikleri** iletişim kutusunda, proje adını yazarak değiştirin `ComObject1` içinde **proje adı** alan.  
  
4.  İçinde **Proje Gezgini**, sağ `Class1`ve ardından **özellikleri**. **Özellikleri** sınıfı penceresi görüntülenir.  
  
5.  Değişiklik `Name` özelliğini `MathFunctions`.  
  
6.  İçinde **Proje Gezgini**, sağ `MathFunctions`ve ardından **kodu görüntüle**. **Kod Düzenleyicisi** görüntülenir.  
  
7.  Özellik değerini tutacak bir yerel değişken ekleyin:  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  Özellik Ekle `Let` ve özellik `Get` özellik yordamları:  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. Bir işlevi ekleyin:  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. Oluşturma ve COM nesnesi tıklayarak kaydetme **olun ComObject1.dll** üzerinde **dosya** menüsü.  
  
    > [!NOTE]
    >  Ayrıca bir COM nesnesi olarak Visual Basic ile oluşturulan bir sınıf getirebilir olsa da, doğru bir COM nesnesi değil ve bu izlenecek yolda kullanılamaz. Ayrıntılar için bkz [.NET Framework uygulamalarında COM birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="interop-assemblies"></a>Birlikte çalışma derlemeleri  
 Aşağıdaki yordamda, yönetilmeyen kod (örneğin, bir COM nesnesi) ve Visual Studio kullanan yönetilen kodu arasında bir köprü görevi gören bir birlikte çalışma derlemesi oluşturur. Visual Basic oluşturur birlikte çalışma derlemesi çoğu, gibi COM nesneleri ile çalışma ayrıntılarını işler *birlikte çalışma hazırlama*, işlem paketleme parametrelerinin ve dönüş değerlerine eşdeğeri veri türleri için geçerken ve COM nesneleri. Visual Basic uygulama başvurusu değil gerçek COM nesnesi birlikte çalışma derlemesine işaret eder.  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Bir COM nesnesi Visual Basic 2005 ve sonraki sürümler ile kullanmak için  
  
1.  Yeni bir Visual Basic Windows uygulaması projesi açın.  
  
2.  Üzerinde **proje** menüsünü tıklatın **Başvuru Ekle**.  
  
     **Başvuru Ekle** iletişim kutusu görüntülenir.  
  
3.  Üzerinde **COM** sekmesinde, çift `ComObject1` içinde **bileşen adı** listelemek ve tıklayın **Tamam**.  
  
4.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
5.  İçinde **şablonları** bölmesinde tıklayın **sınıfı**.  
  
     Varsayılan dosya adı `Class1.vb`, görünür **adı** alan. Bu alan MathClass.vb ve seçeneğini değiştirme **Ekle**. Bu adlı bir sınıf oluşturur `MathClass`ve kendi kodunu görüntüler.  
  
6.  Üstüne aşağıdaki kodu ekleyin `MathClass` COM sınıfından devralmak için.  
  
     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]  
  
7.  Aşağıdaki kodu ekleyerek temel sınıfının ortak yöntemi aşırı `MathClass`:  
  
     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]  
  
8.  Aşağıdaki kodu ekleyerek devralınan sınıf genişletmek `MathClass`:  
  
     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]  
  
 Yeni bir sınıf COM nesnesi içinde temel sınıfın özelliklerini devralır, bir yöntem yüklemeleri ve sınıf genişletmek için yeni bir yöntem tanımlar.  
  
#### <a name="to-test-the-inherited-class"></a>Devralınan sınıf test etmek için  
  
1.  Başlangıç formunuza bir düğme ekleyin ve ardından kendi kodunu görüntülemek için çift tıklayın.  
  
2.  Düğmenin içinde `Click` olay işleyici yordamı, bir örneğini oluşturmak için aşağıdaki kodu ekleyin `MathClass` ve aşırı yüklenmiş yöntemler çağırabilirsiniz:  
  
     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]  
  
3.  F5 tuşuna basarak projeyi çalıştırın.  
  
 Formunda, düğmeyi tıklattığınızda `AddNumbers` yöntemi ile ilk kez çağrıldığında `Short` sayı veri türü ve Visual Basic, temel sınıftan uygun yöntemi seçer. İçin yapılan ikinci çağrı `AddNumbers` aşırı yükleme yöntemini yönlendirildiği `MathClass`. Üçüncü çağrı çağrıları `SubtractNumbers` sınıfını genişleten bir yöntem. Temel sınıf özelliği ayarlanmış ve değeri görüntülenir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Fark etmiş Aşırı yüklenen `AddNumbers` işlevi aynı veri COM nesnesinin temel sınıftan devralınan yöntemi olarak türüne sahip görünür. Temel sınıf yönteminin parametreleri ve bağımsız değişkenler, Visual Basic 6.0 16-bit tamsayılar olarak tanımlanır, ancak 16-bit tamsayı türü olarak kullanıma sunulur çünkü `Short` Visual Basic'in daha sonraki sürümleri. Yeni işlev 32-bit tamsayı kabul eder ve temel sınıf işlev aşırı.  
  
 COM nesneleriyle çalışırken, parametre boyutunu ve veri türlerini doğruladığınızdan emin olun. Örneğin, bir Visual Basic 6.0 koleksiyon nesnesi bağımsız değişken olarak kabul eden bir COM nesnesi kullandığınızda, Visual Basic'in sonraki bir sürümünü koleksiyonundan sağlayamaz.  
  
 Özellikler ve yöntemler COM sınıflardan devralınan bir yerel özellik veya değiştiren bir özellik veya temel bir COM sınıftan devralınan yöntemini bildirebilirsiniz anlamı kılınabilir. Devralınan COM özellikleri geçersiz kılmak için kuralları, diğer özellikleri ve yöntemleri aşağıdaki istisnalar dışında geçersiz kılmak için kurallar benzerdir:  
  
-   Herhangi bir özelliği veya bir COM sınıftan devralınan yöntemi geçersiz kılarsanız, tüm diğer devralınan özellikleri ve yöntemleri geçersiz kılmanız gerekir.  
  
-   Kullandığınız özellikler `ByRef` parametreleri geçersiz kılınamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Inherits Deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Short Veri Türü](../../../visual-basic/language-reference/data-types/short-data-type.md)
