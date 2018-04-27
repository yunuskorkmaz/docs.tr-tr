---
title: "İzlenecek yol: Windows API'larını Çağırma (Visual Basic)"
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 34bfb732e2d99b259811573a427ae66628c7fc3a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>İzlenecek yol: Windows API'larını Çağırma (Visual Basic)
Windows, Windows işletim sisteminin parçası olan dinamik bağlantı kitaplıklarını (DLL'ler) apı'leridir. Bunları kendi eşdeğer yordamları yazmak zor olduğu durumlarda görevleri gerçekleştirmek için kullanın. Örneğin, Windows adlı bir işlev sağlar `FlashWindowEx` olanak tanıyan bir uygulama için başlık çubuğu açık ve koyu gri arasında alternatif olun.  
  
 Windows API'ları kodunuzda kullanmanın avantajı, zaten yazılır yararlı işlevleri onlarca ve kullanılacak bekleme içerdiğinden bunlar geliştirme zaman kazanabilirsiniz ' dir. Windows API ile ve unforgiving şeyler ters gittiğinde iş zor olabilir olumsuz olur.  
  
 Windows API'ları birlikte çalışabilirlik özel kategorisini temsil eder. Windows API'ları, yönetilen kod kullanmaz, tür kitaplıkları ve Visual Studio ile kullanılanlardan farklı veri türlerini kullanan yerleşik sahip değil. Bu farklılıklar nedeniyle ve Windows API'ları COM nesneleri, Windows API ile birlikte çalışabilirlik olmadığından ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] platformu kullanılarak gerçekleştirilen çağırma, veya PInvoke. Platform çağırma etkinleştirir DLL'lerde uygulanan yönetilmeyen işlevleri çağırmak için kodu yönetilen bir hizmettir. Daha fazla bilgi için bkz: [yönetilmeyen DLL işlevlerini kullanma](../../../framework/interop/consuming-unmanaged-dll-functions.md). Visual Basic'te PInvoke kullanarak kullanabilirsiniz `Declare` bildirimi veya uygulama `DllImport` özniteliği için boş bir yordamı.  
  
 Windows API çağrıları, Visual Basic geçmişte programlama önemli bir parçası olan, ancak nadiren Visual Basic .NET ile gereklidir. Mümkün olduğunda, yönetilen koddan kullanması gereken [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Windows API çağrıları yerine görevleri gerçekleştirmek için. Bu kılavuzda hangi kullanarak bu durumlar için bilgiler sağlar Windows API'ları gereklidir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>API çağrıları kullanarak bildirme  
 Windows API'leri çağırmak için en yaygın yolu kullanmaktır `Declare` deyimi.  
  
#### <a name="to-declare-a-dll-procedure"></a>DLL yordamı bildirmek için  
  
1.  Aramak istediğiniz işlevi artı bağımsız değişkenler, bağımsız değişken türleri adını belirlemek ve değeri yanı sıra adını ve konumunu içerdiği DLL döndürür.  
  
    > [!NOTE]
    >  Windows API'ları hakkında tam bilgi için Platform SDK Windows API içinde Win32 SDK belgelerine bakın. Windows API'leri kullanan sabitleri hakkında daha fazla bilgi için Platform SDK'sı ile dahil Windows.h gibi üstbilgi dosyalarını inceleyin.  
  
2.  Yeni bir Windows uygulama projesi tıklatarak **yeni** üzerinde **dosya** menüsüne ve ardından **proje**. **Yeni proje** iletişim kutusu görüntülenir.  
  
3.  Seçin **Windows uygulaması** Visual Basic proje şablonları listesinden. Yeni Proje görüntülenir.  
  
4.  Aşağıdakileri ekleyin `Declare` sınıfı veya modül DLL kullanmak istediğiniz işlev:  
  
     [!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### <a name="parts-of-the-declare-statement"></a>Bölümlerini Declare deyimi  
 `Declare` Deyimi aşağıdaki öğeleri içerir.  
  
#### <a name="auto-modifier"></a>Otomatik değiştiricisi  
 `Auto` Değiştiricisi ortak dil çalışma zamanı kurallarını (veya belirtilen diğer ad) göre yöntemi adına dayalı dizeyi dönüştürmek için çalışma zamanı bildirir.  
  
#### <a name="lib-and-alias-keywords"></a>LIB ve diğer anahtar sözcükler  
 Ad aşağıdaki `Function` anahtar sözcüğü, programınızın kullandığı alınan işlevine erişmek için adıdır. Çağırdığınız işlevinin gerçek adıyla aynı olabilir ya da herhangi bir geçerli yordam adı ve ardından employ kullanabileceğiniz `Alias` anahtar çağırdığınız işlevi gerçek adını belirtin.  
  
 Belirtin `Lib` anahtar sözcüğünü, çağırdığınız işlevi içeren dll Dosyasının konumunu ve adını. Windows Sistem dizinlerde bulunan dosyaların yolunu belirtmeniz gerekmez.  
  
 Kullanım `Alias` işlevin adını, arıyorsanız, anahtar sözcüğü geçerli bir Visual Basic yordamı adı değil ya da diğer öğeler, uygulamanızın adı ile çakışıyor. `Alias` Çağrılan işlev doğru adını gösterir.  
  
#### <a name="argument-and-data-type-declarations"></a>Bağımsız değişken ve veri türü bildirimleri  
 Bağımsız değişkenler ve kendi veri türleri bildirin. Windows kullanan veri türleri Visual Studio veri türlerine karşılık gelmediğinden bu bölümü zor olabilir. Visual Basic mu çok fazla iş sizin için uyumlu veri türleri, adlı bir işlem bağımsız değişkenleri dönüştürerek *hazırlama*. Bağımsız değişkenler kullanarak nasıl sıralanmış açıkça kontrol edebilirsiniz <xref:System.Runtime.InteropServices.MarshalAsAttribute> tanımlanan öznitelik <xref:System.Runtime.InteropServices> ad alanı.  
  
> [!NOTE]
>  Visual Basic önceki sürümlerini parametreleri bildirmek izin `As Any`, bu verileri tüm verilerin anlamı türü kullanılabilir. Visual Basic gerektirir, belirli bir veri türüne tüm kullanmanızı `Declare` deyimleri.  
  
#### <a name="windows-api-constants"></a>Windows API sabitleri  
 Bazı bağımsız değişkenler sabitleri birleşimleridir. Örneğin, `MessageBox` bu kılavuzda gösterilen API adlı tamsayı bağımsız değişken kabul `Typ` ileti kutusu nasıl görüntüleneceğini denetler. Bu sabitleri sayısal değerini inceleyerek belirleyebilirsiniz `#define` WinUser.h dosyasındaki ifadelerini. Dolayısıyla ekleyip ondalık biçime dönüştürmek için bir hesap makinesi kullanmak isteyebilirsiniz sayısal değerleri genellikle onaltılık olarak gösterilir. Örneğin, ünlem işareti stili için sabitleri birleştirmek istiyorsanız `MB_ICONEXCLAMATION` 0x00000030 ve Evet/stil yok `MB_YESNO` 0x00000004, sayıları ve bir sonuç 0x00000034 ya da 52 ondalık almak. Ondalık sonuç doğrudan kullanabilmenize karşın, bu değerleri, uygulamanızda sabitleri olarak bildirin ve bunları birleştirmek daha iyi kullanarak `Or` işleci.  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>Windows API çağrıları için sabitleri bildirmek için  
  
1.  Aradığınız Windows işlevi için belgelere bakın. Kullandığı sabitleri adını ve bu sabitleri için sayısal değerleri içeren .h dosyasının adını belirler.  
  
2.  Üstbilgi (.h) dosyasının içeriğini görüntülemek için Not Defteri gibi bir metin düzenleyicisi kullanın ve kullandığınız sabitler ile ilişkili değerleri bulur. Örneğin, `MessageBox` API'sini kullanan sabiti `MB_ICONQUESTION` ileti kutusunda bir soru işareti göstermek için. Tanımı `MB_ICONQUESTION` içinde WinUser.h ve aşağıdaki gibi görünür:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  Eşdeğer bir gruba eklemek `Const` deyimleri sınıfına veya bu sabitleri uygulamanızı kullanılabilir hale getirmek için modülü. Örneğin:  
  
     [!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### <a name="to-call-the-dll-procedure"></a>DLL yordam çağrısı için  
  
1.  Adlı bir düğme ekleme `Button1` başlangıç için form projeniz için ve kendi kod görüntülemek için çift tıklayın. Düğme için olay işleyicisini görüntülenir.  
  
2.  Kodu ekleyin `Click` eklediğiniz, yordam çağrısı ve uygun bağımsız değişkenlerini sağlamak için düğmesi olay işleyicisi:  
  
     [!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  F5 tuşuna basarak projeyi çalıştırın. İleti kutusu ikisi ile görüntülenen **Evet** ve **Hayır** yanıt düğmeler. Bunlardan birini tıklatın.  
  
#### <a name="data-marshaling"></a>Veri hazırlama  
 Visual Basic veri türleri için parametreler ve dönüş değerleri Windows API çağrıları otomatik olarak dönüştürür ancak kullanabilirsiniz `MarshalAs` bir API bekliyor yönetilmeyen veri türleri açıkça belirtmek için özniteliği. Birlikte çalışma hazırlama hakkında daha fazla bilgi için bkz: [birlikte çalışma hazırlama](../../../framework/interop/interop-marshaling.md).  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Declare ve MarshalAs bir API çağrısında kullanmak için  
  
1.  Veri türleri, bağımsız değişkenlerini aramak istediğiniz işlevin adını belirlemek ve dönüş değeri.  
  
2.  Erişimi kolaylaştırmak için `MarshalAs` özniteliği, ekleme bir `Imports` sınıfı veya aşağıdaki örnekteki gibi modülü için kod üstüne deyimi:  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  Sınıf veya kullanıyorsanız ve uygulama modülü içeri aktarılan işlevi için bir işlev prototipi eklemek `MarshalAs` özniteliği parametreleri veya dönüş değeri. Aşağıdaki örnekte, türü bir API çağrısı `void*` olarak sıralanmış `AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## <a name="api-calls-using-dllimport"></a>DllImport kullanarak API çağrıları  
 `DllImport` Özniteliği tür kitaplıklarının DLL'lerde işlevleri çağırmak için ikinci bir yol sağlar. `DllImport` kullanmaya kabaca eşdeğerdir bir `Declare` deyimi ancak işlevler nasıl çağrılır üzerinde daha fazla denetim sağlar.  
  
 Kullanabileceğiniz `DllImport` ile çoğu Windows API çağrıları çağrı paylaşılan bir başvuruyor sürece (bazen adlı *statik*) yöntemi. Sınıfının bir örneği gerekli yöntemlerini kullanamazsınız. Farklı `Declare` deyimleri `DllImport` çağrıları kullanamaz `MarshalAs` özniteliği.  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>DllImport özniteliği kullanılarak bir Windows API'si çağırmak için  
  
1.  Yeni bir Windows uygulama projesi tıklatarak **yeni** üzerinde **dosya** menüsüne ve ardından **proje**. **Yeni proje** iletişim kutusu görüntülenir.  
  
2.  Seçin **Windows uygulaması** Visual Basic proje şablonları listesinden. Yeni Proje görüntülenir.  
  
3.  Adlı bir düğme ekleme `Button2` başlangıç formu.  
  
4.  Çift `Button2` form için kod görünümünü açın.  
  
5.  Erişimi kolaylaştırmak için `DllImport`, ekleme bir `Imports` başlangıç formu sınıfı için kod üstüne deyimi:  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  Önceki bir boş işlevi bildirme `End Class` deyimi form ve adını işlevi için `MoveFile`.  
  
7.  Uygulama `Public` ve `Shared` değiştiricileri için parametreleri ayarlama ve işlev bildirimi için `MoveFile` Windows API işlevi kullanır bağımsız değişkenleri göre:  
  
     [!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     İşlevinizi herhangi bir geçerli yordam adı olabilir; `DllImport` özniteliği dll Dosyasının adını belirtir. Birlikte çalışabilirlik için parametreleri hazırlama aynı zamanda işleyen ve verileri benzer Visual Studio veri türleri seçebilmeniz dönüş değerleri türlerden API kullanır.  
  
8.  Uygulama `DllImport` özniteliği boş işlevi. İlk parametre, aradığınız işlevi içeren dll Dosyasının konumunu ve adını ' dir. Windows Sistem dizinlerde bulunan dosyaların yolunu belirtmeniz gerekmez. İkinci parametre Windows API işlevin adını belirten bir adlandırılmış bağımsız değişkenidir. Bu örnekte, `DllImport` özniteliği zorlar çağrıları `MoveFile` iletilmesi için `MoveFileW` KERNEL32 içinde. DLL. `MoveFileW` Yöntemi kopyalar bir dosya yolu `src` yoluna `dst`.  
  
     [!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. Kodu ekleyin `Button2_Click` bir işlevi çağırmak için olay işleyicisi:  
  
     [!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. Sınama.txt adlı bir dosya oluşturun ve bunu sabit diskinizde C:\Tmp dizinine yerleştirir. Gerekirse Tmp dizini oluşturun.  
  
11. Uygulamayı başlatmak için F5 tuşuna basın. Ana form görüntülenir.  
  
12. Tıklatın **Button2**. Dosyayı taşıdıysanız "dosyası başarıyla taşındı" iletisi görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)  
 [Diğer ad](../../../visual-basic/language-reference/statements/alias-clause.md)  
 [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Yönetilen Kodda Prototipler Oluşturma](../../../framework/interop/creating-prototypes-in-managed-code.md)  
 [Geri Çağırma Yöntemi Olarak Bir Temsilci Hazırlama](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
