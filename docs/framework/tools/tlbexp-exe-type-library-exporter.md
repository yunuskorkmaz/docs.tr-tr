---
title: Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)
ms.date: 03/30/2017
helpviewer_keywords:
- exporting type library [.NET Framework]
- exporter tool [.NET Framework]
- Tlbexp.exe
- Type Library Exporter
- type libraries [.NET Framework], exporting
ms.assetid: a487d61b-d166-467b-a7ca-d8b52fbff42d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 843b791177b57134483a7076dbc6ec979956ef60
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421861"
---
# <a name="tlbexpexe-type-library-exporter"></a>Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)
Tür Kitaplığı Verme Programı, bir ortak dil çalışma zamanı derlemesinde tanımlanan türleri açıklayan bir tür kitaplığı üretir.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
tlbexp assemblyName [options]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*AssemblyName*|Bir tür kitaplığının kendisi için dışarı aktarılacağı derleme.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ asmpath:** *dizini*|Derlemelerin aranacağı konumu belirtir. Bu seçeneği kullanırsanız, geçerli dizini de dahil olmak üzere, başvurulan derlemelerin aranacağı konumları açıkça belirtmeniz gerekir.<br /><br /> Kullanırken **asmpath** seçeneği, tür kitaplığı dışarı Aktarıcı aramaz bir derlemeyi genel derleme önbelleğinde (GAC).|  
|**/ Help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/ adları:** *dosya adı*|Bir tür kitaplığındaki adların büyük küçük harfle nasıl yazılacağını belirtir. *Filename* bağımsız değişkeni bir metin dosyasıdır. Dosyadaki her bir satır, tür kitaplığındaki bir adın büyük küçük harfle nasıl yazılacağını belirtir.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/oldnames**|Bir tür adı çakışması varsa, Tlbexp.exe'yi donatılmış tür adlarını dışarı aktarmaya zorlar. .NET Framework sürüm 2.0'dan önceki sürümlerde varsayılan davranışın bu olduğunu unutmayın.|  
|**/ out:** *dosyası*|Üretilecek tür kitaplığı dosyasının adını belirtir. Bu seçeneği atlarsanız, Tlbexp.exe, derlemeyle (derlemeyi içeren dosyayla aynı olması gerekmeyen, gerçek derleme adı) aynı adda ve .tlb uzantılı bir tür kitaplığı üretir.|  
|**/silence:** `warningnumber`|Belirtilen uyarının görüntülenmesini bastırır. Bu seçenek kullanılamaz **/silent**.|  
|**/silent**|Başarı iletilerinin görüntülenmesini bastırır. Bu seçenek kullanılamaz **/sessiz**.|  
|**/tlbreference:** *typelibraryname*|Tlbexp.exe'yi, kayıt defterine danışmadan tür kitaplığı başvurularını açıkça çözmeye zorlar. Örneğin, derleme B derleme A'ya başvurursa, kayıt defterinde belirtilen tür kitaplığına güvenmek yerine, bir açık tür kitaplığı başvurusu sağlamak için bu seçeneği kullanabilirsiniz. Tlbexp.exe, tür kitaplığı sürümünün derleme sürümüyle eşleşmesini sağlamak için bir sürüm denetimi yapar; tersi durumda, bir hata üretir.<br /><br /> Unutmayın **defterine başvurduğunu** seçeneği hala kayıt durumlarda danışır burada <xref:System.Runtime.InteropServices.ComImportAttribute> özniteliği, ardından başka bir tür tarafından gerçekleştirilen bir arabirime uygulanır.|  
|**/tlbrefpath:** *yolu*|Başvurulan tür kitaplığının tam olarak belirtilen yolu.|  
|**/win32**|64 bit'lik bir bilgisayarda derleme yaparken, bu seçenek Tlbexp.exe'nin bir 32 bit tür kitaplığı ürettiğini belirtir.|  
|**/Win64**|32-bit bir bilgisayarda derleme yaparken, bu seçenek Tlbexp.exe'nin bir 64 bit tür kitaplığı ürettiğini belirtir.|  
|**/verbose**|Ayrıntılı modu belirtir; kendileri için bir tür kitaplığı üretilmesi gereken tüm başvurulan derlemelerin listesini görüntüler.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
>  Tlbexp.exe için komut satırı seçenekleri büyük-küçük harfe duyarlıdır ve herhangi bir sırada sağlanabilir. Tek yapmanız gereken, onu benzersiz şekilde tanımlamak için seçeneği yeterince belirtmektir. Örneğin, **/n** eşdeğerdir **/nologo**, ve **/o:** *outfile.tlb* eşdeğerdir **/out:**  *OutFile.tlb*.  
  
## <a name="remarks"></a>Açıklamalar  
 Tlbexp.exe, derlemede tanımlanan türlerin tanımlarını içeren bir tür kitaplığı üretir. Visual Basic 6.0 gibi uygulamalar, derlemede tanımlanan .NET türlerine bağlanacak üretilmiş tür kitaplığını kullanabilir.  
  
> [!IMPORTANT]
>  Windows meta veri (.winmd) dosyalarını dışarı aktarmak için Tlbexp.exe'yi kullanamazsınız. Windows Çalışma Zamanı derlemelerinin dışarı aktarılması desteklenmez.  
  
 Tüm derleme bir kez dönüştürülür. Derlemede tanımlanan türlerin bir alt kümesi için tür bilgisi üretmek üzere Tlbexp.exe'yi kullanamazsınız.  
  
 Kullanılarak içeri aktarılan bir derlemeden bir tür kitaplığı üretmek için Tlbexp.exe'yi kullanamazsınız [tür kitaplığı alma programı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Onun yerine, Tlbimp.exe ile içeri aktarılan özgün tür kitaplığına başvurmanız gerekir. Tlbimp.exe kullanılarak içeri aktarılan derlemelere başvuran bir derlemeden bir tür kitaplığını içeri aktarabilirsiniz. Aşağıdaki örnekler bölümüne bakın.  
  
 Tlbexp.exe, üretilen tür kitaplıklarını geçerli çalışma dizinine veya çıktı dosyası için belirtilen dizine yerleştirir. Tek bir derleme, birçok tür kitaplığının üretilmesine neden olabilir.  
  
 Tlbexp.exe bir tür kitaplığı oluşturur ama bunu kaydetmez. Tersine budur [derleme Kayıt Aracı (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md), hangi hem üreten hem tür kitaplığını kaydeder. COM ile bir tür kitaplığı üretmek ve kaydetmek için, Regasm.exe'yi kullanın.  
  
 Ya da belirtmezseniz `/win32` veya `/win64` seçeneği, Tlbexp.exe, bilgisayar üzerinde yapmakta olduğunuz derleme (32 bit veya 64 bit bilgisayar) türüne karşılık gelen bir 32 bit veya 64 bit tür kitaplığı üretir. Çapraz derleme amaçları için kullanabileceğiniz `/win64` ve 64 bit tür kitaplığı üretmek için bir 32-bit bilgisayarda seçeneği kullanabilirsiniz `/win32` 64-bit bilgisayarda 32 bit tür kitaplığı üretmek için seçeneği. 32 bit tür kitaplıklarında <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> değeri ayarı <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>. 64 bit tür kitaplıklarında <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> değeri ayarı <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>. Tüm veri türü Dönüşümleri (örneğin, gibi işaretçi boyutlu veri türleri `IntPtr` ve `UIntPtr`) uygun şekilde dönüştürülür.  
  
 Kullanırsanız <xref:System.Runtime.InteropServices.MarshalAsAttribute> belirtmek için özniteliği bir <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> değerini `VT_UNKOWN` veya `VT_DISPATCH`, Tlbexp.exe, sonraki tüm kullanımlarını yoksayar <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> alan. Örneğin, aşağıdaki imzalar verildiğinde:  
  
```  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_UNKNOWN, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructUnkSafe(){return null;}  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_DISPATCH, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructDispSafe(){return null;}  
```  
  
 aşağıdaki tür kitaplığı oluşturulur:  
  
```  
[id(0x60020004)]  
HRESULT StructUnkSafe([out, retval] SAFEARRAY(IUnknown*)* pRetVal);  
[id(0x60020005)]  
HRESULT StructDispSafe([out, retval] SAFEARRAY(IDispatch*)* pRetVal);  
```  
  
 Tlbexp.exe yoksayar Not <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> alan.  
  
 Tür kitaplıkları derlemelerde bulunan tüm bilgileri barındıramayacağından, dışarı aktarma işlemi sırasında Tlbexp.exe bazı verileri atabilir. Dönüştürme işleminin açıklaması ve her bir tür kitaplığına yayılan bilgi parçasının kaynağının tanımlaması için bkz: [tür kitaplığına dönüştürme özeti derlemeye](https://msdn.microsoft.com/library/3a37eefb-a76c-4000-9080-7dbbf66a4896).  
  
 Tür kitaplığı dışarı Aktarıcı içeren yöntemleri dışarı Not <xref:System.TypedReference> parametre olarak `VARIANT`rağmen <xref:System.TypedReference> nesnenin yönetilmeyen kodda hiçbir anlamı vardır. İçeren yöntemleri dışarı aktardığınızda <xref:System.TypedReference> parametreleri, tür kitaplığı verme programı bir uyarı üretmez veya hata ve sonuçta elde edilen tür kitaplığını kullanan yönetilmeyen kod doğru şekilde çalışmaz.  
  
 Tür Kitaplığı Verme Programı Microsoft Windows 2000 ve sonraki sürümlerde desteklenir.  
  
## <a name="examples"></a>Örnekler  
 Derleme içinde bulunan aşağıdaki komutu, aynı ada sahip bir tür kitaplığı üretir. `myTest.dll`.  
  
```  
tlbexp myTest.dll  
```  
  
 Aşağıdaki komut ada sahip bir tür kitaplığı üretir `clipper.tlb`.  
  
```  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 Aşağıdaki örnekte, bir tür kitaplığını Tlbimp.exe kullanılarak içeri aktarılan derlemelere başvuran bir derlemeden dışarı aktarmak için Tlbexp.exe'nin kullanılması gösterilmektedir.  
  
 İlk tür kitaplığını içeri aktarmak için Tlbimp.exe kullanın `myLib.tlb` ve kaydedileceği `myLib.dll`.  
  
```  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 Aşağıdaki komutu, derlemek için C# derleyicisini kullanır. `Sample.dll,` başvuran `myLib.dll` önceki örnekte oluşturulan.  
  
```  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 Aşağıdaki komut için bir tür kitaplığı üretir `Sample.dll` başvuran `myLib.dll`.  
  
```  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.TypeLibExporterFlags>  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Regasm.exe (Derleme Kayıt Aracı)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)  
 [Derlemeden tür kitaplığına dönüştürme özeti](https://msdn.microsoft.com/library/3a37eefb-a76c-4000-9080-7dbbf66a4896)  
 [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
