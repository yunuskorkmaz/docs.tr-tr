---
title: Sabitler ve Numaralandırmalar (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: ec314f78cf4c22c39d1ce41a7623bb4891f6ecd0
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774864"
---
# <a name="constants-and-enumerations-visual-basic"></a>Sabitler ve Numaralandırmalar (Visual Basic)
Visual Basic, geliştiriciler için bir dizi önceden tanımlanmış sabitler ve numaralandırmalar sağlar. Sabitler, bir uygulamanın yürütülmesi boyunca sabit kalan değerleri depolar. Numaralandırmalar ilgili sabitler kümesiyle çalışmanın kolay bir yolunu sağlar ve sabit değerleri adlarla ilişkilendirir.  
  
## <a name="constants"></a>Sabitler  
  
### <a name="conditional-compilation-constants"></a>Koşullu derleme sabitleri  
 Aşağıdaki tabloda koşullu derleme için kullanılabilen önceden tanımlanmış sabitler listelenmektedir.  
  
|**Sabit**|**Açıklama**|  
|---|---|  
|`CONFIG`|**Configuration Manager** **etkin çözüm yapılandırma** kutusunun geçerli ayarına karşılık gelen bir dize.|  
|`DEBUG`|**Proje özellikleri** iletişim kutusunda ayarlankullanılabilecek bir `Boolean` değeri. Varsayılan olarak, bir proje için hata ayıklama yapılandırması `DEBUG`tanımlar. `DEBUG` tanımlandığında, <xref:System.Diagnostics.Debug> sınıf yöntemleri **Çıkış** penceresinde çıkış oluşturur. Tanımlanmadığı zaman, <xref:System.Diagnostics.Debug> sınıf yöntemleri derlenmez ve hata ayıklama çıkışı oluşturulmaz.|  
|`TARGET`|Proje için çıkış türünü temsil eden bir dize veya komut satırı **/target** seçeneğinin ayarı. `TARGET` olası değerleri şunlardır:<br /><br /> -bir Windows uygulaması için "winexe".<br />-konsol uygulaması için-"exe".<br />-bir sınıf kitaplığı için "Library".<br />-bir modül için "Module".<br />- **/Target** seçeneği Visual Studio tümleşik geliştirme ortamında ayarlanabilir. Daha fazla bilgi için bkz. [-target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|**Proje özellikleri** iletişim kutusunda ayarlankullanılabilecek bir `Boolean` değeri. Varsayılan olarak, bir proje için tüm yapılandırmaların `TRACE`tanımlar. `TRACE` tanımlandığında, <xref:System.Diagnostics.Trace> sınıf yöntemleri **Çıkış** penceresinde çıkış oluşturur. Tanımlı olmadığında <xref:System.Diagnostics.Trace> sınıf yöntemleri derlenmez ve hiçbir `Trace` çıkışı oluşturulmaz.|  
|`VBC_VER`|Visual Basic sürümünü *büyük*olarak temsil eden bir sayı. *küçük* biçim.|  
  
### <a name="print-and-display-constants"></a>Yazdırma ve görüntüleme sabitleri  
 Yazdırma ve görüntüleme işlevlerini çağırdığınızda kodunuzda gerçek değerleri yerine aşağıdaki sabitleri kullanabilirsiniz.  
  
|**Sabit**|**Açıklama**|  
|---|---|  
|`vbCrLf`|Satır başı/linefeed karakter birleşimi.|  
|`vbCr`|Satır başı karakteri.|  
|`vbLf`|Linefeed karakteri.|  
|`vbNewLine`|Yeni satır karakteri.|  
|`vbNullChar`|Null karakter.|  
|`vbNullString`|Sıfır uzunluklu dize ("") ile aynı değil; Dış yordamları çağırmak için kullanılır.|  
|`vbObjectError`|Hata numarası. Kullanıcı tanımlı hata numaraları bu değerden büyük olmalıdır. Örneğin:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Sekme karakteri.|  
|`vbBack`|Geri al karakteri.|  
|`vbFormFeed`|Microsoft Windows 'da kullanılmaz.|  
|`vbVerticalTab`|Microsoft Windows 'da yararlı değildir.|  
  
## <a name="enumerations"></a>Numaralandırmalar  
 Aşağıdaki tabloda Visual Basic tarafından sunulan numaralandırmalar listelenmektedir ve açıklanmaktadır.  
  
|Sabit Listesi|Açıklama|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|<xref:Microsoft.VisualBasic.Interaction.Shell%2A> işlevi çağrılırken çağrılan program için kullanılacak pencere stilini gösterir.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Ses yöntemleri çağrılırken seslerin nasıl çalındığını gösterir.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> yöntemi çağrılırken denetlenecek rolün türünü gösterir.|  
|<xref:Microsoft.VisualBasic.CallType>|<xref:Microsoft.VisualBasic.Interaction.CallByName%2A> işlevi çağrılırken çağrılan yordamın türünü gösterir.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Karşılaştırma işlevleri çağrılırken dizelerin nasıl karşılaştırılacağını gösterir.|  
|<xref:Microsoft.VisualBasic.DateFormat>|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> işlevi çağrılırken tarihlerin nasıl görüntüleneceğini gösterir.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Tarih ile ilgili işlevleri çağırırken tarih aralıklarını belirleme ve biçimlendirme işlemlerinin nasıl yapılacağını gösterir.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Silinecek bir dizin dosya veya dizin içerdiğinde ne yapılması gerektiğini belirtir.|  
|<xref:Microsoft.VisualBasic.DueDate>|Mali Yöntemler çağrılırken ödemelerin ne zaman beklediğini gösterir.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Metin alanlarının sınırlanmış mi yoksa sabit mi olduğunu gösterir.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Dosya erişim işlevleri çağrılırken kullanılacak dosya özniteliklerini gösterir.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Tarih ile ilgili işlevler çağrılırken kullanılacak haftanın ilk gününü gösterir.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Tarih ile ilgili işlevler çağrılırken kullanılacak yılın ilk haftasını gösterir.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlevi tarafından döndürülen bir ileti kutusunda hangi düğmeye basıldığını gösterir.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlevi çağrılırken hangi düğmelerin görüntüleneceğini gösterir.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Dosya erişimi işlevlerini çağırırken bir dosyanın nasıl açılacağını gösterir.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Dosya erişimi işlevlerini çağırırken bir dosyanın nasıl açılacağını gösterir.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Dosya erişimi işlevlerini çağırırken bir dosyanın nasıl açılacağını gösterir.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Bir dosyanın kalıcı olarak silinip silinmeyeceğini veya geri dönüşüm kutusu 'na yerleştirilip yerleştirilmeyeceğini belirtir.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Tüm veya en üst düzey dizinlerin aranıp aranmayacağını belirtir.|  
|<xref:Microsoft.VisualBasic.TriState>|`Boolean` bir değeri veya sayı biçimlendirme işlevleri çağrılırken varsayılan değerin kullanılıp kullanılmayacağını belirtir.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Kullanıcı bir işlem sırasında **iptal** ' i tıklarsa ne yapılması gerektiğini belirtir.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Dosya veya dizinleri kopyalarken, silerken veya taşırken ilerleme durumu iletişim kutusunun gösterilip gösterilmeyeceğini belirtir.|  
|<xref:Microsoft.VisualBasic.VariantType>|<xref:Microsoft.VisualBasic.Information.VarType%2A> işlevi tarafından döndürülen bir değişken nesnesinin türünü gösterir.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|<xref:Microsoft.VisualBasic.Strings.StrConv%2A> işlevi çağrılırken gerçekleştirilecek dönüştürme türünü gösterir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Dili Başvurusu](../../visual-basic/language-reference/index.md)
- [Visual Basic](../../visual-basic/index.md)
- [Sabitlere Genel Bakış](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Sabit Listelerine Genel Bakış](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
