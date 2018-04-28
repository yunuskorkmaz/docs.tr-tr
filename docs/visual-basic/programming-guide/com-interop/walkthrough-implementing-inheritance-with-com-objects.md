---
title: 'İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b03b81c9e04e79f8ce7763ecf8a489d248ff480b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama (Visual Basic)
Visual Basic sınıflardan türetilemeyeceğini `Public` olanlar Visual Basic önceki sürümlerinde oluşturulan COM nesnelerini sınıflarda. Özellikleri ve yöntemleri COM nesneleri devralınan sınıfların geçersiz kılındı gibi özellikleri olarak aşırı yüklendi ve herhangi bir taban sınıf yöntemlerini geçersiz veya aşırı yüklenmiş. COM nesneleri içinden devralma yeniden derleyin istemediğiniz varolan bir sınıf kitaplığı olduğunda yararlıdır.  
  
 Aşağıdaki yordamda, Visual Basic 6.0 bir sınıfı içeren bir COM nesnesi oluşturmak ve temel sınıf olarak kullanmak gösterilmiştir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>Bu kılavuzda kullanılan COM nesnesi oluşturmak için  
  
1.  Visual Basic 6. 0'da, yeni bir ActiveX DLL projesi açın. Adlı bir proje `Project1` oluşturulur. Adlı bir sınıf sahip `Class1`.  
  
2.  İçinde **Proje Gezgini**, sağ **Project1**ve ardından **Project1 özellikleri**. **Proje özelliklerini** iletişim kutusu görüntülenir.  
  
3.  Üzerinde **genel** sekmesinde **proje özelliklerini** iletişim kutusunda, proje adını yazarak değiştirme `ComObject1` içinde **proje adı** alan.  
  
4.  İçinde **Proje Gezgini**, sağ `Class1`ve ardından **özellikleri**. **Özellikleri** sınıfı için penceresi görüntülenir.  
  
5.  Değişiklik `Name` özelliğine `MathFunctions`.  
  
6.  İçinde **Proje Gezgini**, sağ `MathFunctions`ve ardından **görünümü kodu**. **Kod düzenleyicisinde** görüntülenir.  
  
7.  Özellik değeri tutmak için yerel bir değişken ekleyin:  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  Özellik ekleme `Let` ve özellik `Get` özellik yordamları:  
  
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
  
10. Oluşturma ve tıklayarak COM nesnesi kaydetme **olun ComObject1.dll** üzerinde **dosya** menüsü.  
  
    > [!NOTE]
    >  Ayrıca bir COM nesnesi olarak Visual Basic ile oluşturulan bir sınıf getirebilir rağmen doğru bir COM nesnesi değil ve bu kılavuzda kullanılamaz. Ayrıntılar için bkz [.NET Framework uygulamalarında COM birlikte çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="interop-assemblies"></a>Birlikte çalışma derlemeleri  
 Aşağıdaki yordamda, yönetilmeyen kod (örneğin, bir COM nesnesi) ve Visual Studio kullanan yönetilen kod arasında bir köprü görevi gören bir birlikte çalışma derlemesi oluşturur. Visual Basic oluşturur birlikte çalışma derlemesi birçok gibi COM nesneleri ile çalışma ayrıntılarını işler *birlikte çalışma hazırlama*, işlemi paketleme parametreler ve dönüş değerleri eşdeğer veri türleri için taşırken ve COM nesneleri. Visual Basic uygulama nokta derlemesine başvuru birlikte çalışma, gerçek COM nesnesi değil.  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Visual Basic 2005 ve sonraki sürümler ile COM nesnesini kullanma  
  
1.  Yeni bir Visual Basic Windows uygulama projesi açın.  
  
2.  Üzerinde **proje** menüsünde tıklatın **Başvuru Ekle**.  
  
     **Başvuru Ekle** iletişim kutusu görüntülenir.  
  
3.  Üzerinde **COM** sekmesinde, çift `ComObject1` içinde **bileşen adı** listesinde ve tıklatın **Tamam**.  
  
4.  Üzerinde **proje** menüsünde tıklatın **Yeni Öğe Ekle**.  
  
     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
5.  İçinde **şablonları** bölmesinde tıklatın **sınıfı**.  
  
     Varsayılan dosya adı `Class1.vb`, görünür **adı** alan. Bu alan MathClass.vb tıklatın geçip **Ekle**. Bu adlı bir sınıf oluşturur `MathClass`ve kendi kod görüntüler.  
  
6.  En üst kısmına aşağıdaki kodu ekleyin `MathClass` COM sınıfından için.  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  Aşağıdaki kodu ekleyerek temel sınıfın genel yöntem aşırı `MathClass`:  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  Aşağıdaki kodu ekleyerek devralınan sınıfını genişleten `MathClass`:  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 Yeni sınıf COM nesnesi temel sınıfının özelliklerini devralır, bir yöntemi aşırı yüklemeleri ve sınıf genişletmek için yeni bir yöntemi tanımlar.  
  
#### <a name="to-test-the-inherited-class"></a>Devralınan sınıfı test etmek için  
  
1.  Düğme başlangıç formunuza eklemek ve kendi kod görüntülemek için çift tıklatın.  
  
2.  Düğmenin içinde `Click` olay işleyicisi yordamı, bir örneğini oluşturmak için aşağıdaki kodu ekleyin `MathClass` ve aşırı yüklenmiş yöntemler çağırın:  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  F5 tuşuna basarak projeyi çalıştırın.  
  
 Form düğmeyi tıkladığınızda `AddNumbers` yöntemi ile çağrılmadan önce `Short` veri türü numaraları ve Visual Basic temel sınıfından uygun yöntemi seçer. İkinci çağrı `AddNumbers` aşırı yükleme yönteminden yönlendirildiği `MathClass`. Üçüncü çağrıları çağrı `SubtractNumbers` sınıfını genişleten yöntemi. Taban sınıfı özelliğinde ayarlanır ve değer görüntülenir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Fark etmiş aşırı yüklenmiş `AddNumbers` işlevi aynı veri türünde COM nesnesinin temel sınıfından devralınan yöntemi olarak görünür. Visual Basic 6.0 16 bit tamsayı olarak bağımsız değişkenleri ve parametreleri temel sınıf yönteminin tanımlı, ancak türü 16 bit tamsayı olarak gösterilir çünkü `Short` Visual Basic sonraki sürümlerinde. Yeni işlev 32-bit tamsayı kabul eder ve temel sınıf işlevi overloads.  
  
 COM nesneleri ile çalışırken, parametre boyut ve veri türlerini doğruladığınızdan emin olun. Örneğin, bir Visual Basic 6.0 koleksiyon nesnesi bağımsız değişken olarak kabul eden bir COM nesnesi kullanırken, Visual Basic daha sonraki bir sürümü koleksiyondan sağlayamaz.  
  
 Özellikleri ve yöntemleri COM sınıflardan devralınan bir yerel özellik veya bir özellik değiştiren veya temel bir COM sınıfından devralınan yöntemini bildirebilir anlamı kılınabilir. Devralınan COM özelliklerini geçersiz kılma kuralları, diğer özellikleri ve yöntemleri aşağıdaki istisnalar dışında geçersiz kılma için kurallar benzerdir:  
  
-   Herhangi bir özelliği veya bir COM sınıfından devralınan yöntemi geçersiz kılarsanız, tüm diğer devralınan özellikleri ve yöntemleri geçersiz kılması gerekir.  
  
-   Kullandığınız özellikler `ByRef` parametreleri geçersiz kılınamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Inherits Deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Short Veri Türü](../../../visual-basic/language-reference/data-types/short-data-type.md)
