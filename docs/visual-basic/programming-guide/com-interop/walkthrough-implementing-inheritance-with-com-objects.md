---
title: 'İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: bdb891e1a150f0d7b79aefcc3db1f18dc8e84be4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396733"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama (Visual Basic)

`Public`Visual Basic önceki sürümlerinde oluşturulanlar da dahil olmak üzere COM nesnelerinde sınıflardan Visual Basic sınıfları türetebilirsiniz. COM nesnelerinden devralınan sınıfların özellikleri ve yöntemleri, özellik olarak geçersiz kılınabilir veya aşırı yüklenebilir ve diğer temel sınıfların yöntemlerinin geçersiz kılınabilmesi veya aşırı yüklenmesi olabilir. COM nesnelerinden devralma, yeniden derlemek istemediğiniz mevcut bir sınıf kitaplığınız olduğunda faydalıdır.

Aşağıdaki yordamda, bir sınıfı içeren COM nesnesi oluşturmak için Visual Basic 6,0 ' nin nasıl kullanılacağı gösterilmektedir ve ardından bunu temel sınıf olarak kullanın.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>Bu kılavuzda kullanılan COM nesnesini oluşturmak için

1. Visual Basic 6,0 ' de, yeni bir ActiveX DLL projesi açın. Adlı bir proje `Project1` oluşturulur. Adında bir sınıfı vardır `Class1` .

2. **Proje Gezgini**'Nde, **Project1**öğesine sağ tıklayın ve ardından **Project1 özellikleri**' ne tıklayın. **Proje özellikleri** iletişim kutusu görüntülenir.

3. Proje **özellikleri** Iletişim kutusunun **genel** sekmesinde Proje adı alanına yazarak proje adını değiştirin `ComObject1` . **Project Name**

4. **Proje Gezgini**'nde, öğesine sağ tıklayın `Class1` ve ardından **Özellikler**' e tıklayın. Sınıfının **Özellikler** penceresi görüntülenir.

5. `Name`Özelliğini olarak değiştirin `MathFunctions` .

6. **Proje Gezgini**'nde, öğesine sağ tıklayın `MathFunctions` ve ardından **kodu görüntüle**' ye tıklayın. **Kod Düzenleyicisi** görüntülenir.

7. Özellik değerini tutacak bir yerel değişken ekleyin:

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. Özellik `Let` ve özellik `Get` özelliği yordamlarını ekleyin:

    ```vb
    Public Property Let Prop1(ByVal vData As Integer)
       'Used when assigning a value to the property.
       mvarProp1 = vData
    End Property
    Public Property Get Prop1() As Integer
       'Used when retrieving a property's value.
       Prop1 = mvarProp1
    End Property
    ```

9. Bir işlev ekleyin:

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. **Dosya** menüsündeki **ComObject1. dll** ' ye tıklayarak com nesnesi oluşturun ve kaydedin.

    > [!NOTE]
    > Ayrıca, Visual Basic ile oluşturulmuş bir sınıfı bir COM nesnesi olarak kullanıma sunabilseniz de, bu, gerçek bir COM nesnesi değildir ve bu kılavuzda kullanılamaz. Ayrıntılar için bkz. [.NET Framework uygulamalarda com birlikte çalışabilirliği](com-interoperability-in-net-framework-applications.md).

## <a name="interop-assemblies"></a>Birlikte çalışma derlemeleri

Aşağıdaki yordamda, yönetilmeyen kod (COM nesnesi gibi) ve Visual Studio 'Nun kullandığı yönetilen kod arasında köprü görevi gören bir birlikte çalışma derlemesi oluşturacaksınız. Visual Basic tarafından oluşturulan birlikte çalışma derlemesi, *birlikte çalışma hazırlama*ve com nesnelerinden gelen ve bunlara geçiş yaparken değerleri eşdeğer veri türlerine döndürme gibi com nesneleriyle çalışma hakkında pek çok ayrıntıyı işler. Visual Basic uygulamasındaki başvuru, gerçek COM nesnesi değil birlikte çalışma derlemesine işaret eder.

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Visual Basic 2005 ve sonraki sürümlerde bir COM nesnesi kullanmak için

1. Yeni bir Visual Basic Windows uygulaması projesi açın.

2. **Proje** menüsünde, **Başvuru Ekle**' ye tıklayın.

     **Başvuru Ekle** iletişim kutusu görüntülenir.

3. **Com** sekmesinde, `ComObject1` **bileşen adı** listesine çift tıklayın ve **Tamam**' a tıklayın.

4. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.

5. **Şablonlar** bölmesinde **sınıf**' a tıklayın.

     Varsayılan dosya adı, `Class1.vb` **ad** alanında görünür. Bu alanı MathClass. vb olarak değiştirin ve **Ekle**' ye tıklayın. Bu, adlı bir sınıf oluşturur `MathClass` ve kodunu görüntüler.

6. COM sınıfından devralması için aşağıdaki kodu en üst öğesine ekleyin `MathClass` .

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. Aşağıdaki kodu öğesine ekleyerek temel sınıfın ortak yöntemini aşırı yükleme `MathClass` :

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. Aşağıdaki kodu öğesine ekleyerek devralınan sınıfı genişletin `MathClass` :

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

Yeni sınıf COM nesnesindeki temel sınıfın özelliklerini devralır, bir yöntemi aşırı yükler ve sınıfı genişletmek için yeni bir yöntem tanımlar.

### <a name="to-test-the-inherited-class"></a>Devralınan sınıfı test etmek için

1. Başlangıç formunuza bir düğme ekleyin ve sonra kodunu görüntülemek için çift tıklayın.

2. Düğmenin `Click` olay işleyicisi yordamında, örneği oluşturmak `MathClass` ve aşırı yüklenmiş yöntemleri çağırmak için aşağıdaki kodu ekleyin:

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. F5 tuşuna basarak projeyi çalıştırın.

Formdaki düğmeye tıkladığınızda, `AddNumbers` yöntemi ilk olarak `Short` veri türü numaralarıyla çağırılır ve Visual Basic temel sınıftan uygun yöntemi seçer. İkinci çağrısı, ' `AddNumbers` den aşırı yükleme yöntemine yönlendirilir `MathClass` . Üçüncü çağrı, `SubtractNumbers` sınıfını genişleten yöntemini çağırır. Temel sınıftaki özelliği ayarlanır ve değer görüntülenir.

## <a name="next-steps"></a>Sonraki Adımlar

Aşırı yüklenmiş `AddNumbers` işlevin, com nesnesinin temel sınıfından devralınan yöntemle aynı veri türüne sahip olduğunu fark etmiş olabilirsiniz. Bunun nedeni, temel sınıf yönteminin bağımsız değişkenlerinin ve parametrelerinin Visual Basic 6,0 ' de 16 bit tamsayılar olarak tanımlandığından, ancak Visual Basic sonraki sürümlerinde türünün 16 bit tamsayılar olarak sunulmasıdır `Short` . Yeni işlev 32 bitlik tamsayılar kabul eder ve temel sınıf işlevini aşırı yükler.

COM nesneleriyle çalışırken, parametrelerin boyutunu ve veri türlerini doğruladığınızdan emin olun. Örneğin, bir bağımsız değişken olarak Visual Basic 6,0 koleksiyon nesnesini kabul eden bir COM nesnesi kullanırken, Visual Basic daha sonraki bir sürümünden koleksiyon sağlayamezsiniz.

COM sınıflarından devralınan özellikler ve Yöntemler geçersiz kılınabilir, yani bir temel COM sınıfından devralınan bir özelliğin veya yöntemin yerini alan bir yerel özellik veya yöntem bildirebilmeniz anlamına gelir. Devralınan COM özelliklerinin üzerine yazma kuralları, diğer özellikleri ve yöntemleri aşağıdaki özel durumlarla geçersiz kılmak için kurallara benzerdir:

- Bir COM sınıfından devralınan herhangi bir özelliği veya yöntemi geçersiz kılarsınız, diğer devralınmış özellikleri ve yöntemleri geçersiz kılmanız gerekir.

- Parametreleri kullanan özellikler `ByRef` geçersiz kılınamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği](com-interoperability-in-net-framework-applications.md)
- [Inherits Deyimi](../../language-reference/statements/inherits-statement.md)
- [Short Veri Türü](../../language-reference/data-types/short-data-type.md)
