---
title: "İzlenecek yol: Windows API'lerini Çağırma"
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
ms.openlocfilehash: c7b84a3bb12329ae235e5ea03dc5e86f921112c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396759"
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>İzlenecek yol: Windows API'larını Çağırma (Visual Basic)
Windows API 'Leri, Windows işletim sisteminin bir parçası olan dinamik bağlantı kitaplıkları (dll). Bunları kendi kendine eşdeğer prosedürleri yazmak zor olduğunda görevleri gerçekleştirmek için kullanabilirsiniz. Örneğin, Windows, `FlashWindowEx` açık ve koyu gölgeler arasında bir uygulama için başlık çubuğunu yapmanızı sağlayan adlı bir işlev sağlar.  
  
 Kodunuzda Windows API 'Lerini kullanmanın avantajı, önceden yazılmış ve kullanılması bekleyen çok sayıda faydalı işlev içerdiğinden, geliştirme süresini kaydedebildiğinden. Olumsuz bir deyişle, Windows API 'Lerinin, bir şeyler doğru olduğunda ve bu işlemleri geri almak zor olabilir.  
  
 Windows API 'Leri, birlikte çalışabilirlik özel kategorisini temsil eder. Windows API 'Leri yönetilen kod kullanmaz, yerleşik tür kitaplıkları yoktur ve Visual Studio ile kullanılandan farklı veri türlerini kullanır. Bu farklılıklar nedeniyle ve Windows API 'Leri COM nesneleri olmadığından, Windows API 'Leri ile birlikte çalışabilirlik ve .NET Framework platform Invoke veya PInvoke kullanılarak gerçekleştirilir. Platform çağırma, yönetilen kodun DLL 'lerde uygulanan yönetilmeyen işlevleri çağırmasına olanak sağlayan bir hizmettir. Daha fazla bilgi için bkz. [YÖNETILMEYEN DLL işlevlerini](../../../framework/interop/consuming-unmanaged-dll-functions.md)kullanma. Visual Basic ' de, `Declare` ifadesini kullanarak veya `DllImport` özniteliğini boş bir yordama uygulayarak, PInvoke kullanabilirsiniz.  
  
 Windows API çağrıları geçmişte Visual Basic Programlamanın önemli bir parçasıdır, ancak Visual Basic .NET ile nadiren gerekli değildir. Mümkün olduğunda, Windows API çağrıları yerine görevleri gerçekleştirmek için .NET Framework yönetilen kodu kullanmanız gerekir. Bu izlenecek yol, Windows API 'Lerini kullanmanın gerekli olduğu durumlar hakkında bilgi sağlar.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>Declare kullanan API çağrıları  
 Windows API 'Lerini çağırmak için en yaygın yol, `Declare` ifadesini kullanmaktır.  
  
### <a name="to-declare-a-dll-procedure"></a>Bir DLL yordamı bildirmek için  
  
1. Çağırmak istediğiniz işlevin adını, ayrıca bağımsız değişkenlerini, bağımsız değişken türlerini ve dönüş değerini ve onu içeren DLL 'nin adını ve konumunu saptayın.  
  
    > [!NOTE]
    > Windows API 'Leri hakkında tüm bilgiler için, Platform SDK 'Sı Windows API 'sindeki Win32 SDK belgelerine bakın. Windows API 'Lerinin kullandığı sabitler hakkında daha fazla bilgi için Platform SDK 'sına dahil edilen Windows. h gibi üst bilgi dosyalarını inceleyin.  
  
2. **Dosya** menüsünde **Yeni** ' ye ve ardından **Proje**' ye tıklayarak yeni bir Windows uygulaması projesi açın. **Yeni Proje** iletişim kutusu görünür.  
  
3. Visual Basic proje şablonları listesinden **Windows uygulaması** ' nı seçin. Yeni proje görüntülenir.  
  
4. Aşağıdaki işlevi, `Declare` DLL 'yi kullanmak istediğiniz sınıfa veya modüle ekleyin:  
  
     [!code-vb[VbVbalrInterop#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#9)]  
  
### <a name="parts-of-the-declare-statement"></a>Declare Ifadesinin kısımları  
 `Declare`Bu ifade aşağıdaki öğeleri içerir.  
  
#### <a name="auto-modifier"></a>Otomatik değiştirici  
 `Auto`Değiştirici, çalışma zamanına, ortak dil çalışma zamanı kurallarına (veya belirtilmişse diğer ad) göre Yöntem adına göre dize dönüştürmesini söyler.  
  
#### <a name="lib-and-alias-keywords"></a>Lib ve Alias anahtar sözcükleri  
 Anahtar sözcüğünü izleyen ad, `Function` programınızın içeri aktarılan işleve erişmek için kullandığı addır. Bu, aradığınız işlevin gerçek adı ile aynı olabilir veya herhangi bir geçerli yordam adı kullanabilir ve sonra, `Alias` Aradığınız işlevin gerçek adını belirtmek için anahtar sözcüğünü kullanabilirsiniz.  
  
 `Lib`Anahtar sözcüğünü ve ardından, aradığınız işlevi IÇEREN dll 'nin adını ve konumunu belirtin. Windows sistem dizinlerinde bulunan dosyaların yolunu belirtmeniz gerekmez.  
  
 `Alias`Aradığınız işlevin adı geçerli bir Visual Basic yordam adı değilse veya uygulamanızdaki diğer öğelerin adı ile çakışıyorsa, anahtar sözcüğünü kullanın. `Alias`çağrılan işlevin doğru adını gösterir.  
  
#### <a name="argument-and-data-type-declarations"></a>Bağımsız değişken ve veri türü bildirimleri  
 Bağımsız değişkenleri ve veri türlerini bildirin. Bu bölüm, Windows 'un kullandığı veri türleri Visual Studio veri türlerine karşılık gelmediğinden zor olabilir. Visual Basic, değişkenleri *sıralama*adlı bir işlem olan uyumlu veri türlerine dönüştürerek sizin için çok sayıda iş yapar. <xref:System.Runtime.InteropServices.MarshalAsAttribute>Ad alanında tanımlanan özniteliği kullanarak bağımsız değişkenlerin nasıl sıralanarak açıkça kontrol edebilirsiniz <xref:System.Runtime.InteropServices> .  
  
> [!NOTE]
> Önceki Visual Basic sürümleri, parametreleri bildirmenize izin `As Any` ver, yani herhangi bir veri türü verisinin kullanılabileceği anlamına gelir. Visual Basic, tüm deyimler için belirli bir veri türü kullanmanızı gerektirir `Declare` .  
  
#### <a name="windows-api-constants"></a>Windows API sabitleri  
 Bazı bağımsız değişkenler sabitler birleşimleridir. Örneğin, `MessageBox` Bu izlenecek yolda gösterilen API, `Typ` ileti kutusunun nasıl görüntülendiğini denetleyen adlı bir tamsayı bağımsız değişkenini kabul eder. WinUser. h dosyasındaki deyimleri inceleyerek, bu sabitlerin sayısal değerini belirleyebilirsiniz `#define` . Sayısal değerler genellikle onaltılı olarak gösterilir, bu nedenle bunları eklemek ve Decimal 'a dönüştürmek için bir Hesaplayıcı kullanmak isteyebilirsiniz. Örneğin, ünlem stili `MB_ICONEXCLAMATION` 0x00000030 ve Evet/Hayır stili `MB_YESNO` 0x00000004 olan sabitleri birleştirmek istiyorsanız, sayıları ekleyebilir ve 0x00000034 veya 52 ondalık sonucunu elde edebilirsiniz. Ondalık sonucunu doğrudan kullanabilseniz de, bu değerleri uygulamanızda sabitler olarak bildirmek ve işlecini kullanarak birleştirmek daha iyidir `Or` .  
  
##### <a name="to-declare-constants-for-windows-api-calls"></a>Windows API çağrıları için sabitleri bildirmek için  
  
1. Aradığınız Windows işlevine yönelik belgelere başvurun. Kullandığı sabitlerin adını ve bu sabitler için sayısal değerleri içeren. h dosyasının adını saptayın.  
  
2. Not Defteri gibi bir metin düzenleyicisini kullanarak üst bilgi (. h) dosyasının içeriğini görüntüleyin ve kullandığınız sabitler ile ilişkili değerleri bulun. Örneğin, API, `MessageBox` `MB_ICONQUESTION` ileti kutusunda bir soru işareti göstermek için sabiti kullanır. Tanımı `MB_ICONQUESTION` WinUser. h ' dir ve şu şekilde görünür:  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3. `Const`Bu sabitleri uygulamanız için kullanılabilir hale getirmek için sınıfınıza veya modülünüzü eşdeğer deyimler ekleyin. Örnek:  
  
     [!code-vb[VbVbalrInterop#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#11)]  
  
###### <a name="to-call-the-dll-procedure"></a>DLL yordamını çağırmak için  
  
1. `Button1`Projeniz için başlangıç formuna adlı bir düğme ekleyin ve sonra kodunu görüntülemek için çift tıklayın. Düğme için olay işleyicisi görüntülenir.  
  
2. `Click`Yordamı çağırmak ve uygun bağımsız değişkenleri sağlamak için, eklediğiniz düğmenin olay işleyicisine kod ekleyin:  
  
     [!code-vb[VbVbalrInterop#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#12)]  
  
3. F5 tuşuna basarak projeyi çalıştırın. İleti kutusu hem **Evet** hem de yanıt düğmesi **olmadan** görüntülenir. Birine tıklayın.  
  
#### <a name="data-marshaling"></a>Veri sıralama  
 Visual Basic, Windows API çağrıları için parametrelerin veri türlerini ve dönüş değerlerini otomatik olarak dönüştürür, ancak `MarshalAs` BIR API 'nin beklediği yönetilmeyen veri türlerini açıkça belirtmek için özniteliğini kullanabilirsiniz. Birlikte çalışabilirlik sıralaması hakkında daha fazla bilgi için bkz. [Interop Marshal](../../../framework/interop/interop-marshaling.md).  
  
##### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Bir API çağrısında Declare ve MarshalAs kullanmak için  
  
1. Çağırmak istediğiniz işlevin adını, ayrıca bağımsız değişkenlerini, veri türlerini ve dönüş değerini saptayın.  
  
2. Özniteliğe erişimi basitleştirmek için `MarshalAs` , `Imports` Aşağıdaki örnekte olduğu gibi sınıf veya modül için kodun en üstüne bir ifade ekleyin:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
3. İçeri aktarılan işlev için, kullandığınız sınıfa veya modüle bir işlev prototipi ekleyin ve `MarshalAs` özniteliği parametrelere veya dönüş değerine uygulayın. Aşağıdaki örnekte, türü bekleyen bir API çağrısı `void*` şöyle sıralanır `AsAny` :  
  
     [!code-vb[VbVbalrInterop#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#14)]  
  
## <a name="api-calls-using-dllimport"></a>DllImport kullanan API çağrıları  
 `DllImport`Özniteliği, dll 'lerdeki işlevleri tür kitaplıkları olmadan çağırmak için ikinci bir yol sağlar. `DllImport`, bir deyimin kullanımı için kabaca eşdeğerdir, `Declare` ancak işlevlerin nasıl çağrıldığı üzerinde daha fazla denetim sağlar.  
  
 `DllImport`Çağrı paylaşılan (bazen *statik*olarak adlandırılır) yöntemine başvurduğu sürece, çoğu Windows API çağrısı ile kullanabilirsiniz. Bir sınıf örneği gerektiren yöntemleri kullanamazsınız. `Declare`Deyimlerden farklı olarak, `DllImport` çağrılar `MarshalAs` özniteliği kullanamaz.  
  
### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>DllImport özniteliğini kullanarak bir Windows API 'SI çağırmak için  
  
1. **Dosya** menüsünde **Yeni** ' ye ve ardından **Proje**' ye tıklayarak yeni bir Windows uygulaması projesi açın. **Yeni Proje** iletişim kutusu görünür.  
  
2. Visual Basic proje şablonları listesinden **Windows uygulaması** ' nı seçin. Yeni proje görüntülenir.  
  
3. Başlangıç formuna adlı bir düğme ekleyin `Button2` .  
  
4. `Button2`Form için kod görünümünü açmak üzere çift tıklayın.  
  
5. Erişimini basitleştirmek için `DllImport` , `Imports` Başlangıç Form sınıfı için kodun en üstüne bir ifade ekleyin:  
  
     [!code-vb[VbVbalrInterop#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#13)]  
  
6. Form için olan deyimden önceki boş bir işlev bildirin `End Class` ve işlevi adlandırın `MoveFile` .  
  
7. `Public` `Shared` İşlev bildirimine ve değiştiricilerini uygulayın ve `MoveFile` Windows API işlevinin kullandığı bağımsız değişkenlere göre parametreleri ayarlayın:  
  
     [!code-vb[VbVbalrInterop#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#16)]  
  
     İşleviniz geçerli bir yordam adına sahip olabilir; `DllImport`öznitelik, dll 'de adı belirtir. Ayrıca parametreler ve dönüş değerleri için birlikte çalışabilirlik sıralamasını işler, böylece API 'nin kullandığı veri türlerine benzer Visual Studio veri türlerini seçebilirsiniz.  
  
8. `DllImport`Özniteliği boş işleve uygulayın. İlk parametre, aradığınız işlevi içeren DLL 'nin adı ve konumudur. Windows sistem dizinlerinde bulunan dosyaların yolunu belirtmeniz gerekmez. İkinci parametre, Windows API 'sindeki işlevin adını belirten adlandırılmış bir bağımsız değişkendir. Bu örnekte, `DllImport` ÖZNITELIĞI `MoveFile` Kernel32 içinde öğesine iletime çağrısı yapılmasını zorlar `MoveFileW` . Dosyasını. `MoveFileW`Yöntemi yolu yolundan bir dosya kopyalar `src` `dst` .  
  
     [!code-vb[VbVbalrInterop#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#17)]  
  
9. `Button2_Click`İşlevi çağırmak için olay işleyicisine kod ekleyin:  
  
     [!code-vb[VbVbalrInterop#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#18)]  
  
10. Test. txt adlı bir dosya oluşturun ve sabit sürücünüzdeki C:\Tmp dizinine yerleştirin. Gerekirse, tmp dizinini oluşturun.  
  
11. Uygulamayı başlatmak için F5 tuşuna basın. Ana form görüntülenir.  
  
12. **Button2**'ye tıklayın. Dosya taşınabilmesi durumunda "dosya başarıyla taşındı" iletisi görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Declare Deyimi](../../language-reference/statements/declare-statement.md)
- [Otomatik](../../language-reference/modifiers/auto.md)
- [Ek](../../language-reference/statements/alias-clause.md)
- [COM birlikte çalışma](index.md)
- [Yönetilen Kodda Prototipler Oluşturma](../../../framework/interop/creating-prototypes-in-managed-code.md)
- [Geri Çağırma Yöntemi Olarak Bir Temsilci Hazırlama](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
