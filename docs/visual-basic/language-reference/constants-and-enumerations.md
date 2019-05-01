---
title: Sabitler ve Numaralandırmalar (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: 0a9c01269e12c2d84be4f30c236c439012a88153
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013913"
---
# <a name="constants-and-enumerations-visual-basic"></a>Sabitler ve Numaralandırmalar (Visual Basic)
Visual Basic önceden tanımlı sabitler ve numaralandırmalar geliştiriciler için sunar. Sabitler, bir uygulamanın yürütülmesini sabit kalması değerlerini depolar. Numaralandırmalar ilgili sabitlerinin kümeleri ile birlikte çalışır ve adları ile sabit değerleri ilişkilendirmek için kullanışlı bir yol sağlar.  
  
## <a name="constants"></a>Sabitler  
  
### <a name="conditional-compilation-constants"></a>Koşullu derleme sabitleri  
 Koşullu derleme için kullanılabilen önceden tanımlanmış sabitleri aşağıdaki tabloda listelenmektedir.  
  
|**Sabit**|**Açıklama**|  
|---|---|  
|`CONFIG`|Geçerli ayarına karşılık gelen bir dize **etkin çözüm yapılandırması** kutusunda **Configuration Manager**.|  
|`DEBUG`|A `Boolean` ayarlanabilir değer **proje özellikleri** iletişim kutusu. Varsayılan olarak, bir proje için hata ayıklama yapılandırmasını tanımlar `DEBUG`. Zaman `DEBUG` tanımlanan <xref:System.Diagnostics.Debug> sınıfı yöntemleri oluşturmak için çıkış **çıkış** penceresi. Bu tanımlı değil, <xref:System.Diagnostics.Debug> sınıfı yöntemleri derlenmemiş ve hata ayıklama çıktı oluşturulur.|  
|`TARGET`|Proje veya komut satırı ayarına ilişkin çıktı türünü temsil eden bir dize **/target** seçeneği. Olası değerleri `TARGET` şunlardır:<br /><br /> -bir Windows uygulaması için "winexe".<br />-bir konsol uygulaması için "exe".<br />-bir sınıf kitaplığı için "library".<br />-bir modül için "modülünü".<br />- **/Target** seçeneği, Visual Studio tümleşik geliştirme ortamında ayarlanmış olması. Daha fazla bilgi için [/target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|A `Boolean` ayarlanabilir değer **proje özellikleri** iletişim kutusu. Varsayılan olarak, bir proje için tüm yapılandırmaları tanımlar `TRACE`. Zaman `TRACE` tanımlanan <xref:System.Diagnostics.Trace> sınıfı yöntemleri oluşturmak için çıkış **çıkış** penceresi. Bu tanımlı değil, <xref:System.Diagnostics.Trace> sınıfı yöntemleri derlenmemiş ve Hayır `Trace` çıkış üretilir.|  
|`VBC_VER`|İçinde Visual Basic sürümünü temsil eden bir sayı *ana*. *küçük* biçimi. Sürüm numarası [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] 8.0.|  
  
### <a name="print-and-display-constants"></a>Yazdırma ve görüntü sabitleri  
 Yazdırma arama ve görüntüleme işlevleri, gerçek değerleri yerine kodunuzun içinde aşağıdaki sabitler kullanabilirsiniz.  
  
|**Sabit**|**Açıklama**|  
|---|---|  
|`vbCrLf`|Satır başı/satır besleme karakter birleşimi.|  
|`vbCr`|Satır başı karakteri.|  
|`vbLf`|Satır besleme karakteri.|  
|`vbNewLine`|Yeni satır karakteri.|  
|`vbNullChar`|Null karakteri.|  
|`vbNullString`|Aynı sıfır uzunlukta bir dize (""); Dış yordam çağırmak için kullanılır.|  
|`vbObjectError`|Hata numarası. Kullanıcı tanımlı hata numaralarını, bu değerden büyük olmalıdır. Örneğin:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Sekme karakteri.|  
|`vbBack`|BACKSPACE karakter.|  
|`vbFormFeed`|Microsoft Windows içinde kullanılmaz.|  
|`vbVerticalTab`|Microsoft Windows olmayan yararlıdır.|  
  
## <a name="enumerations"></a>Numaralandırmalar  
 Aşağıdaki tabloda, listeler ve Visual Basic tarafından sağlanan numaralandırmaları açıklar.  
  
|Sabit Listesi|Açıklama|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Başlatılan program için çağrılırken kullanılacak pencere stilini gösterir <xref:Microsoft.VisualBasic.Interaction.Shell%2A> işlevi.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Ses yöntemleri çağrılırken sesleri çalmak nasıl gösterir.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Çağrılırken denetlemek için rol türünü gösterir <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> yöntemi.|  
|<xref:Microsoft.VisualBasic.CallType>|Yordam çağrıldığında çağrılan türünü gösteren <xref:Microsoft.VisualBasic.Interaction.CallByName%2A> işlevi.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Karşılaştırma işlevleri çağırırken dizeleri karşılaştırmak nasıl gösterir.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Tarihlerin nasıl görüntüleneceğini gösterir çağrılırken <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> işlevi.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Belirlemek ve tarih aralıklarını tarihle ilgili işlevler çağırırken biçimlendirmek nasıl gösterir.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Silinecek bir dizine dosyaları veya dizinleri içerdiğinde ne yapılması gerektiğini belirtir.|  
|<xref:Microsoft.VisualBasic.DueDate>|Ödemelerin ne zaman gösterir finansal yöntemleri çağrılırken.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Sabit genişlikte metin alanları ayrılmış olup olmadığını veya gösterir.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Dosya erişimi işlevleri çağrılırken kullanılacak dosya öznitelikleri gösterir.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Tarih ile ilgili işlevler ararken kullanmak için haftanın ilk gününü belirtir.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Tarih ile ilgili işlevler çağırırken kullanmak için yılın ilk haftası gösterir.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Tarafından döndürülen bir ileti kutusunda hangi düğmeye basıldığını belirtir <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlevi.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Görüntülenecek düğmeleri çağırırken gösterir <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlevi.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Dosya erişimi işlevlerini çağırırken bir dosyayı açmaya nasıl gösterir.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Dosya erişimi işlevlerini çağırırken bir dosyayı açmaya nasıl gösterir.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Dosya erişimi işlevlerini çağırırken bir dosyayı açmaya nasıl gösterir.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Bir dosya kalıcı olarak silinmiş veya Geri Dönüşüm Kutusu'na yerleştirilen belirtir.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Tüm arama belirtir ya da yalnızca en üst düzey dizinleri.|  
|<xref:Microsoft.VisualBasic.TriState>|Belirten bir `Boolean` değer veya varsayılan sayı biçimlendirme işlevlerini çağırırken olup kullanılmalıdır.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Neler olması gerektiğini belirtir. kullanıcı tıklarsa Bitti **iptal** bir işlem sırasında.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|İlerleme iletişim kutusu, kopyalama, silme veya dosyaları veya dizinleri taşıma gösterilip gösterilmeyeceğini belirtir.|  
|<xref:Microsoft.VisualBasic.VariantType>|Tarafından döndürülen bir değişken nesne türünü gösteren <xref:Microsoft.VisualBasic.Information.VarType%2A> işlevi.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Çağrılırken gerçekleştirmek için dönüştürme türünü belirten <xref:Microsoft.VisualBasic.Strings.StrConv%2A> işlevi.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Dili Başvurusu](../../visual-basic/language-reference/index.md)
- [Visual Basic](../../visual-basic/index.md)
- [Sabitlere Genel Bakış](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Sabit Listelerine Genel Bakış](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
