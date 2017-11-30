---
title: "Sabitler ve Numaralandırmalar (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9fd298cc504f9e4faf5205e53ebbf2ee355a21b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="constants-and-enumerations-visual-basic"></a>Sabitler ve Numaralandırmalar (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]önceden tanımlı sabitler ve numaralandırmalar geliştiriciler için bir dizi sağlar. Sabitler uygulama yürütme sabit kalır değerleri depolar. Numaralandırmalar ilgili sabitleri kümeleriyle çalışmak ve sabit değerleri adlarıyla ilişkilendirmek için kolay bir yol sağlamak.  
  
## <a name="constants"></a>Sabitler  
  
### <a name="conditional-compilation-constants"></a>Koşullu derleme sabitleri  
 Koşullu derleme için kullanılabilen önceden tanımlanmış sabitleri aşağıdaki tabloda listelenmektedir.  
  
|**Sabit**|**Açıklama**|  
|---|---|  
|`CONFIG`|Geçerli ayarına karşılık gelen bir dize **etkin çözüm yapılandırması** kutusunda **Configuration Manager**.|  
|`DEBUG`|A `Boolean` ayarlanabilir değer **proje özelliklerini** iletişim kutusu. Varsayılan olarak, bir proje için hata ayıklama yapılandırmasını tanımlayan `DEBUG`. Zaman `DEBUG` tanımlanan <xref:System.Diagnostics.Debug> sınıfı yöntemleri Oluştur çıktıya **çıkış** penceresi. Bunu tanımlı değil, <xref:System.Diagnostics.Debug> sınıfı yöntemleri derlenmemiş ve hiçbir hata ayıklama çıktısı oluşturulur.|  
|`TARGET`|Proje veya komut satırı ayarını için çıktı türünü temsil eden bir dize **/target** seçeneği. Olası değerlerini `TARGET` şunlardır:<br /><br /> -bir Windows uygulaması için "winexe".<br />-bir konsol uygulaması için "exe".<br />-bir sınıf kitaplığı için "kitaplığı".<br />-bir modül için "modülü".<br />- **/Target** seçeneği kümesinde [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] tümleşik geliştirme ortamı. Daha fazla bilgi için bkz: [/target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|A `Boolean` ayarlanabilir değer **proje özelliklerini** iletişim kutusu. Varsayılan olarak, bir proje için tüm yapılandırmaları tanımlamak `TRACE`. Zaman `TRACE` tanımlanan <xref:System.Diagnostics.Trace> sınıfı yöntemleri Oluştur çıktıya **çıkış** penceresi. Bunu tanımlı değil, <xref:System.Diagnostics.Trace> sınıfı yöntemleri derlenmemiş ve no `Trace` çıktı oluşturulur.|  
|`VBC_VER`|Sayı temsil eden bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sürümü, *ana*. *küçük* biçimi. İçin sürüm numarasını [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] 8.0.|  
  
### <a name="print-and-display-constants"></a>Yazdırma ve görüntü sabitleri  
 Yazdırma çağırın ve görüntüleme işlevleri, kodunuzu yerine gerçek değerler aşağıdaki sabitleri kullanabilirsiniz.  
  
|**Sabit**|**Açıklama**|  
|---|---|  
|`vbCrLf`|Satır başı/satır besleme karakter birleşimi.|  
|`vbCr`|Satır başı karakteri.|  
|`vbLf`|Satır besleme karakter.|  
|`vbNewLine`|Yeni satır karakteri.|  
|`vbNullChar`|Null karakter.|  
|`vbNullString`|Aynı sıfır uzunlukta bir dize (""); Dış yordamları çağırmak için kullanılır.|  
|`vbObjectError`|Hata numarası. Kullanıcı tanımlı hata sayılar bu değerden daha büyük olmalıdır. Örneğin:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Sekme karakteri.|  
|`vbBack`|BACKSPACE karakter.|  
|`vbFormFeed`|Microsoft Windows'daki kullanılmaz.|  
|`vbVerticalTab`|Microsoft Windows kullanışlı değil.|  
  
## <a name="enumerations"></a>Numaralandırmalar  
 Aşağıdaki tabloda listelenmekte ve tarafından sağlanan numaralandırmalar açıklanmaktadır [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
|Sabit Listesi|Açıklama|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Çağrılırken başlatılan program için kullanılacak pencere stili gösterir <xref:Microsoft.VisualBasic.Interaction.Shell%2A> işlevi.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Ses yöntemleri çağrılırken ses çalınmaya nasıl gösterir.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Çağrılırken denetlemek için rol türünü gösterir <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> yöntemi.|  
|<xref:Microsoft.VisualBasic.CallType>|Yordamı çağrılırken çağrılan türünü gösterir <xref:Microsoft.VisualBasic.Interaction.CallByName%2A> işlevi.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Dizeleri karşılaştırma işlevleri çağrılırken karşılaştırma gösterir.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Tarihleri görüntülemek nasıl gösterir çağrılırken <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> işlevi.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Nasıl belirleyeceğiniz ve ilgili tarihi işlevleri çağırma tarih aralıkları biçimi gösterir.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Silinecek bir dizin dosyaları veya dizinleri içerdiğinde ne yapılması gerektiğini belirtir.|  
|<xref:Microsoft.VisualBasic.DueDate>|Ödemelerin ne zaman gösterir finansal yöntemleri çağrılırken.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Metin alanları olup ayrılmış veya sabit genişlikli gösterir.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Dosya erişim işlevleri ararken kullanılacak dosya öznitelikleri gösterir.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Tarihi ile ilgili işlevleri çağırma sırasında kullanmak için haftanın ilk gününü gösterir.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Tarih ilgili işlevleri çağrılırken kullanmak için yılın ilk haftası gösterir.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Hangi düğmesi tarafından döndürülen bir ileti kutusu üzerinde basıldı gösterir <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlevi.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Çağrılırken görüntülenecek düğmeleri gösterir <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlevi.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Dosya erişim işlevleri çağrılırken bir dosyayı açmaya nasıl gösterir.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Dosya erişim işlevleri çağrılırken bir dosyayı açmaya nasıl gösterir.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Dosya erişim işlevleri çağrılırken bir dosyayı açmaya nasıl gösterir.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Bir dosya kalıcı olarak silinmiş ya da Geri Dönüşüm Kutusu'nda yerleştirilmiş olup olmadığını belirtir.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Tüm arama belirtir veya yalnızca üst düzey dizinleri.|  
|<xref:Microsoft.VisualBasic.TriState>|Gösteren bir `Boolean` değer veya varsayılan sayı biçimlendirme işlevleri çağrılırken kullanılması gerekip gerekmediğini.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Ne olması gerektiğini belirtir kullanıcı tıklarsa Bitti **iptal** bir işlemi sırasında.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Kopyalama, silme veya dosyaları veya dizinleri taşıma ilerleme iletişim kutusu gösterilip gösterilmeyeceğini belirler.|  
|<xref:Microsoft.VisualBasic.VariantType>|Tarafından döndürülen bir değişken nesne türünü belirten <xref:Microsoft.VisualBasic.Information.VarType%2A> işlevi.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Çağrılırken gerçekleştirilecek dönüştürme türünü belirten <xref:Microsoft.VisualBasic.Strings.StrConv%2A> işlevi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic Dil Başvurusu](../../visual-basic/language-reference/index.md)  
 [Visual Basic](../../visual-basic/index.md)  
 [Sabitlere genel bakış](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Numaralandırmalara genel bakış](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
