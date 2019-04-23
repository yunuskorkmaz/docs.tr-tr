---
title: "İzlenecek yol: Windows API'ları çağırma (Visual Basic)"
ms.date: 07/20/2015
helpviewer_keywords:
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls [Visual Basic], walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement [Visual Basic], declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
ms.openlocfilehash: 8fd63c2abedcd416937e2c281486bdc1716a275f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332332"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>İzlenecek yol: Windows API'ları çağırma (Visual Basic)
Windows, Windows işletim sisteminin parçası olan dinamik bağlantı kitaplıklarını (DLL'ler) apı'lerdir. Bunları kendi eşdeğer yordamları yazmak zor olduğunda görevleri gerçekleştirmek için kullanın. Örneğin, Windows adlı bir işlev sağlar `FlashWindowEx` olanak tanıyan bir uygulama için başlık çubuğu arasında açık ve koyu gri alternatif olun.  
  
 Windows API'leri, kodunuzda kullanmanın avantajı, onlarca zaten yazılır kullanışlı işlevi ve kullanılacak bekleme içerdiklerinden, geliştirme süresini kaydedebilirsiniz ' dir. Olumsuz yönüyse, Windows API ile ve unforgiving işler kötüye gittiğinde çalışmaya zor olabilir ' dir.  
  
 Windows API'leri, özel bir kategorinin birlikte çalışabilirlik temsil eder. Windows API'ları, yönetilen kod kullanmayın, yerleşik tür kitaplıklarına ve Visual Studio ile kullanılan farklı veri türlerini kullanma izniniz yok. Bu farklar nedeniyle ve Windows API'leri COM nesneleri, Windows API'ları ile birlikte çalışabilirlik olmadığından ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] platformunu kullanarak gerçekleştirilen çağırmak, veya PInvoke. Platform çağırma etkinleştirir DLL'lerde uygulanan yönetilmeyen işlevleri çağırmak için kod yönetilen bir hizmettir. Daha fazla bilgi için [yönetilmeyen DLL işlevlerini kullanma](../../../framework/interop/consuming-unmanaged-dll-functions.md). Visual Basic'te PInvoke kullanarak kullanabilirsiniz `Declare` deyimi veya uygulama `DllImport` özniteliği için boş bir yordam.  
  
 Windows API çağrıları, Visual Basic programlama geçmişte önemli bir parçası olan, ancak Visual Basic .NET ile nadiren gereklidir. Mümkün olduğunda, yönetilen koddan kullanması gereken [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] görevleri yerine Windows API çağrıları gerçekleştirmek için. Bu izlenecek yolda hangi kullanarak bu durumlar için bilgiler sağlar Windows API'leri gereklidir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>API çağrıları kullanarak bildirin  
 Windows API'leri çağırmak için en yaygın yolu kullanmaktır `Declare` deyimi.  
  
#### <a name="to-declare-a-dll-procedure"></a>Bir DLL yordam bildirmek için  
  
1. Aramak istediğiniz işlevi ek bağımsız değişkenleri, bağımsız değişken türleri adını belirleyin ve değeri yanı sıra adı ve onu içeren DLL konumunu döndürür.  
  
    > [!NOTE]
    >  Windows API'leri hakkında tam bilgi için Platform SDK'sı Windows API Win32 SDK belgelerine bakın. Windows API'leri kullanan sabitleri hakkında daha fazla bilgi için başlık dosyaları gibi Platform SDK'sı ile dahil Windows.h inceleyin.  
  
2. Tıklayarak yeni bir Windows uygulaması projesi açın **yeni** üzerinde **dosya** menüsüne ve ardından **proje**. **Yeni Proje** iletişim kutusu görünür.  
  
3. Seçin **Windows uygulama** Visual Basic proje şablonları listesinden. Yeni Proje görüntülenir.  
  
4. Aşağıdaki `Declare` sınıfı veya modülü DLL kullanmak istediğiniz işlev:  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a>Bölümleri Declare deyimi  
 `Declare` Deyimi aşağıdaki öğeleri içerir.  
  
#### <a name="auto-modifier"></a>Otomatik değiştiricisi  
 `Auto` Değiştiricisi, ortak dil çalışma zamanı kuralları (veya diğer adı belirtilmişse) göre yöntemi adına dayalı dize dönüştürmek için çalışma zamanı bildirir.  
  
#### <a name="lib-and-alias-keywords"></a>LIB ve diğer anahtar sözcükler  
 Adı aşağıdaki `Function` anahtar sözcüğü, programınızın kullandığı içeri aktarılan işlevine erişmek için adıdır. Çağırdığınız işlevin gerçek adıyla aynı olabilir veya herhangi bir geçerli yordam adı ve ardından kullanan kullanabileceğiniz `Alias` anahtar sözcüğünü çağırdığınız işlev gerçek adını belirtin.  
  
 Belirtin `Lib` anahtar sözcüğü, çağırdığınız işlev içeren DLL konumunu ve adını. Dosyalarının Windows Sistem dizinlerde yer alan yolunu belirtmeniz gerekmez.  
  
 Kullanım `Alias` işlevin adını, çağırıyorsanız anahtar sözcüğü geçerli bir Visual Basic yordam adı değil veya diğer öğeleri, uygulamanızın adı ile çakışıyor. `Alias` doğru çağrılan işlevin adını belirtir.  
  
#### <a name="argument-and-data-type-declarations"></a>Bağımsız değişken ve veri tür bildirimleri  
 Bağımsız değişkenler ve veri türlerini bildirin. Bu bölüm Windows kullanan veri türleri için Visual Studio veri türleri karşılık gelmediğinden zor olabilir. Visual Basic birçok iş sizin için yapar adlı bir işlem uyumlu veri türleri için bağımsız değişkenler dönüştürerek *hazırlama*. Bağımsız değişkenleri kullanarak nasıl sıralanmış açıkça denetleyebilirsiniz <xref:System.Runtime.InteropServices.MarshalAsAttribute> tanımlanan öznitelik <xref:System.Runtime.InteropServices> ad alanı.  
  
> [!NOTE]
>  Visual Basic'in önceki sürümlerindeki parametreleri bildirmek izin `As Any`, yani tüm verilerin bu veri türü kullanılabilir. Visual Basic, tüm kullanıcılar için belirli bir veri türüne kullanmanızı gerektirir `Declare` deyimleri.  
  
#### <a name="windows-api-constants"></a>Windows API sabitleri  
 Bazı bağımsız değişkenler, sabitler birleşimleridir. Örneğin, `MessageBox` Bu izlenecek yolda gösterilen API adlı tamsayı bağımsız değişken kabul eden `Typ` ileti kutusunda nasıl görüntülendiğini denetler. Bu sabitler sayısal değerini inceleyerek belirleyebilirsiniz `#define` WinUser.h dosyasındaki deyimler. Ekleyip ondalığa dönüştürmek için bir hesap makinesi kullanmak isteyebilirsiniz sayısal değerleri genellikle onaltılık olarak gösterilir. Örneğin, sabitleri ünlem stili birleştirmek istiyorsanız `MB_ICONEXCLAMATION` 0x00000030 ve Evet/stil `MB_YESNO` 0x00000004, sayıları ve ondalık 0x00000034 veya 52 sonucu alın. Ondalık sonucu doğrudan kullanmanız mümkün olmakla birlikte, sabitler, uygulamanızda bu değerleri bildirir ve bunları birleştirmek daha iyi kullanarak `Or` işleci.  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>Windows API çağrıları için sabitler bildirmek için  
  
1. Aradığınız Windows işlevi belgelerine bakın. Kullandığı sabitleri adını ve bu sabitleri için sayısal değerleri içeren .h dosyası adını belirleyin.  
  
2. Üstbilgi (.h) dosyasının içeriğini görüntülemek için Not Defteri gibi bir metin düzenleyicisi kullanın ve kullandığınız sabitler ile ilişkili değerleri bulur. Örneğin, `MessageBox` API kullanan sabiti `MB_ICONQUESTION` bir soru işareti ileti kutusunda gösterilecek. Tanımı `MB_ICONQUESTION` WinUser.h içinde olan ve aşağıdaki gibi görünür:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. Eşdeğer ekleme `Const` deyimleri sınıfı veya modülü bu sabiti uygulamanızın kullanılabilir hale getirmek için. Örneğin:  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a>DLL yordamı çağırmak için  
  
1. Adlı bir düğme ekleyin `Button1` için başlangıç projeniz için form ve kendi kodunu görüntülemek için çift tıklayın. Düğme için olay işleyicisi görüntülenir.  
  
2. Kodu `Click` eklediğiniz, uygun bağımsız değişkenleri sağlayın ve yordam çağrısı düğmesi için olay işleyicisi:  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. F5 tuşuna basarak projeyi çalıştırın. İleti kutusu ile görüntülenir **Evet** ve **Hayır** yanıt düğmeleri. Bunlardan birini tıklatın.  
  
#### <a name="data-marshaling"></a>Veri hazırlama  
 Visual Basic, parametreler ve dönüş değerleri Windows API çağrıları için veri türlerini otomatik olarak dönüştürür ancak kullanabilirsiniz `MarshalAs` bir API'nin beklediği yönetilmeyen veri türleri açıkça belirtmek için özniteliği. Birlikte çalışma hazırlama hakkında daha fazla bilgi için bkz. [birlikte çalışma hazırlama](../../../framework/interop/interop-marshaling.md).  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Bir API çağrısında bildirin ve MarshalAs kullanmak için  
  
1. Veri türleri, bağımsız değişkenlerinin yanı sıra, çağırmak istediğiniz işlevin adını belirlemek ve dönüş değeri.  
  
2. Erişimini basitleştirmek için `MarshalAs` ekleyin, öznitelik bir `Imports` kod sınıfı veya modülü, aşağıdaki örnekte olduğu gibi en üstüne deyimi:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. İçeri aktarılan işlevine yönelik bir işlev prototipi sınıf veya modül ve uygulama ekleme `MarshalAs` öznitelik parametreleri veya dönüş değeri. Aşağıdaki örnekte, türünü bekleyen bir API çağrısı `void*` olarak sıralanmış `AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a>DllImport kullanarak API çağrıları  
 `DllImport` Özniteliği tür kitaplıklarını DLL'lerde işlevleri çağırmak için ikinci bir yol sağlar. `DllImport` kabaca kullanmakla eşdeğerdir bir `Declare` deyimi ancak işlevlerin çağrılma biçimini üzerinde daha fazla denetim sağlar.  
  
 Kullanabileceğiniz `DllImport` çoğu Windows API ile çağrı paylaşılan bir başvuruyor sürece çağırır (bazen adlı *statik*) yöntemi. Bir sınıf örneği gerektiren yöntemleri kullanamaz. Farklı `Declare` deyimleri `DllImport` çağrıları kullanamaz `MarshalAs` özniteliği.  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>DllImport özniteliği kullanarak bir Windows API çağırmak için  
  
1. Tıklayarak yeni bir Windows uygulaması projesi açın **yeni** üzerinde **dosya** menüsüne ve ardından **proje**. **Yeni Proje** iletişim kutusu görünür.  
  
2. Seçin **Windows uygulama** Visual Basic proje şablonları listesinden. Yeni Proje görüntülenir.  
  
3. Adlı bir düğme ekleyin `Button2` başlangıç formu için.  
  
4. Çift `Button2` formu için kod görünümü açmak için.  
  
5. Erişimini basitleştirmek için `DllImport`, ekleme bir `Imports` başlangıç formu sınıfı için kod üstüne deyimi:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. Önceki boş bir işlevi bildirmek `End Class` form ve işlev adı için bildirimi `MoveFile`.  
  
7. Uygulama `Public` ve `Shared` işlev bildirimi ve kümesi parametreler için değiştiriciler `MoveFile` Windows API işlevi kullanan bağımsız değişkenlerine göre:  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     İşlevinizi herhangi bir geçerli yordamı ad olabilir; `DllImport` özniteliği, DLL Dosyasının adını belirtir. Ayrıca parametreleri birlikte çalışabilirlik hazırlama işler ve verilere benzer olan Visual Studio veri türlerini seçebilmeniz dönüş değerleri türlerini API kullanır.  
  
8. Uygulama `DllImport` özniteliği için boş işlev. İlk parametre, aradığınız işlevi içeren DLL konumunu ve adını ' dir. Dosyalarının Windows Sistem dizinlerde yer alan yolunu belirtmeniz gerekmez. Windows API işlevin adını belirten bir adlandırılmış bağımsız değişken ikinci parametredir. Bu örnekte, `DllImport` özniteliği zorlar çağrıları `MoveFile` iletilmesi için `MoveFileW` KERNEL32 içinde. DLL. `MoveFileW` Yöntemi, bir dosya yolundan kopyalar `src` yoluna `dst`.  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. Kodu `Button2_Click` olay işleyicisi, işlev çağrısı için:  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. Test.txt adlı bir dosya oluşturun ve sabit sürücünüzdeki C:\Tmp dizine yerleştirin. Gerekirse Tmp dizini oluşturun.  
  
11. Uygulamayı başlatmak için F5 tuşuna basın. Ana formu görüntülenir.  
  
12. Tıklayın **Button2**. Dosya taşınabilir "dosya başarıyla taşındı" iletisi görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Diğer ad](../../../visual-basic/language-reference/statements/alias-clause.md)
- [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)
- [Yönetilen Kodda Prototipler Oluşturma](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [Geri Çağırma Yöntemi Olarak Bir Temsilci Hazırlama](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
