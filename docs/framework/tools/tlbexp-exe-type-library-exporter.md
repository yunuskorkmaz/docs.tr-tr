---
title: Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)
description: Tür kitaplığı verme programı Tlbexp.exe gözden geçirin. Bu araç, ortak dil çalışma zamanı (CLR) derlemesinde tanımlanan türleri açıklayan bir tür kitaplığı oluşturur.
ms.date: 03/30/2017
helpviewer_keywords:
- exporting type library [.NET Framework]
- exporter tool [.NET Framework]
- Tlbexp.exe
- Type Library Exporter
- type libraries [.NET Framework], exporting
ms.assetid: a487d61b-d166-467b-a7ca-d8b52fbff42d
ms.openlocfilehash: 3cfaa83590fefe31c437d2ff607fb579aec1da61
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517041"
---
# <a name="tlbexpexe-type-library-exporter"></a>Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)
Tür Kitaplığı Verme Programı, bir ortak dil çalışma zamanı derlemesinde tanımlanan türleri açıklayan bir tür kitaplığı üretir.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
tlbexp assemblyName [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*assemblyName*|Bir tür kitaplığının kendisi için dışarı aktarılacağı derleme.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/asmpath:** *Dizin*|Derlemelerin aranacağı konumu belirtir. Bu seçeneği kullanırsanız, geçerli dizini de dahil olmak üzere, başvurulan derlemelerin aranacağı konumları açıkça belirtmeniz gerekir.<br /><br /> **Asmpath** seçeneğini kullandığınızda, tür kitaplığı verme programı genel derleme ÖNBELLEĞINDE (GAC) bir derleme aramaz.|  
|**/Help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/names:** *filename*|Bir tür kitaplığındaki adların büyük küçük harfle nasıl yazılacağını belirtir. *Filename* bağımsız değişkeni bir metin dosyasıdır. Dosyadaki her bir satır, tür kitaplığındaki bir adın büyük küçük harfle nasıl yazılacağını belirtir.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/oldnames**|Bir tür adı çakışması varsa, Tlbexp.exe'yi donatılmış tür adlarını dışarı aktarmaya zorlar. .NET Framework sürüm 2.0'dan önceki sürümlerde varsayılan davranışın bu olduğunu unutmayın.|  
|**/Out:** *Dosya*|Üretilecek tür kitaplığı dosyasının adını belirtir. Bu seçeneği atlarsanız, Tlbexp.exe, derlemeyle (derlemeyi içeren dosyayla aynı olması gerekmeyen, gerçek derleme adı) aynı adda ve .tlb uzantılı bir tür kitaplığı üretir.|  
|**/sessizlik:**`warningnumber`|Belirtilen uyarının görüntülenmesini bastırır. Bu seçenek **/Silent**ile kullanılamaz.|  
|**/silent**|Başarı iletilerinin görüntülenmesini bastırır. Bu seçenek **/sessizlik**ile kullanılamaz.|  
|**/tlbreference:** *TypeLibraryName*|Tlbexp.exe'yi, kayıt defterine danışmadan tür kitaplığı başvurularını açıkça çözmeye zorlar. Örneğin, derleme B derleme A'ya başvurursa, kayıt defterinde belirtilen tür kitaplığına güvenmek yerine, bir açık tür kitaplığı başvurusu sağlamak için bu seçeneği kullanabilirsiniz. Tlbexp.exe, tür kitaplığı sürümünün derleme sürümüyle eşleşmesini sağlamak için bir sürüm denetimi yapar; tersi durumda, bir hata üretir.<br /><br /> **Tlbreference** seçeneğinin, <xref:System.Runtime.InteropServices.ComImportAttribute> özniteliğin daha sonra başka bir tür tarafından uygulanan bir arabirime uygulandığı durumlarda kayıt defterine hala başvurabileceğini unutmayın.|  
|**/tlbrefpath:** *yol*|Başvurulan tür kitaplığının tam olarak belirtilen yolu.|  
|**/Win32**|64 bit'lik bir bilgisayarda derleme yaparken, bu seçenek Tlbexp.exe'nin bir 32 bit tür kitaplığı ürettiğini belirtir.|  
|**/Win64**|32 bitlik bir bilgisayarda derlerken, bu seçenek Tlbexp.exe 64 bit tür kitaplığı üretmediğini belirtir.|  
|**/verbose**|Ayrıntılı modu belirtir; kendileri için bir tür kitaplığı üretilmesi gereken tüm başvurulan derlemelerin listesini görüntüler.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
> Tlbexp.exe için komut satırı seçenekleri büyük-küçük harfe duyarlıdır ve herhangi bir sırada sağlanabilir. Tek yapmanız gereken, onu benzersiz şekilde tanımlamak için seçeneği yeterince belirtmektir. Örneğin, **/n** **/nologo**ile eşdeğerdir ve **/o:** *çıkışdosyası. tlb* , **/Out:** *çıkışdosyası. tlb*ile eşdeğerdir.  
  
## <a name="remarks"></a>Açıklamalar  
 Tlbexp.exe, derlemede tanımlanan türlerin tanımlarını içeren bir tür kitaplığı üretir. Visual Basic 6.0 gibi uygulamalar, derlemede tanımlanan .NET türlerine bağlanacak üretilmiş tür kitaplığını kullanabilir.  
  
> [!IMPORTANT]
> Windows meta veri (.winmd) dosyalarını dışarı aktarmak için Tlbexp.exe'yi kullanamazsınız. Windows Çalışma Zamanı derlemelerinin dışarı aktarılması desteklenmez.  
  
 Tüm derleme bir kez dönüştürülür. Derlemede tanımlanan türlerin bir alt kümesi için tür bilgisi üretmek üzere Tlbexp.exe'yi kullanamazsınız.  
  
 [Tür kitaplığı alma programı (Tlbimp.exe)](tlbimp-exe-type-library-importer.md)kullanılarak içeri aktarılan bir derlemeden bir tür kitaplığı oluşturmak için Tlbexp.exe kullanamazsınız. Onun yerine, Tlbimp.exe ile içeri aktarılan özgün tür kitaplığına başvurmanız gerekir. Tlbimp.exe kullanılarak içeri aktarılan derlemelere başvuran bir derlemeden bir tür kitaplığını içeri aktarabilirsiniz. Aşağıdaki örnekler bölümüne bakın.  
  
 Tlbexp.exe, üretilen tür kitaplıklarını geçerli çalışma dizinine veya çıktı dosyası için belirtilen dizine yerleştirir. Tek bir derleme, birçok tür kitaplığının üretilmesine neden olabilir.  
  
 Tlbexp.exe bir tür kitaplığı oluşturur ama bunu kaydetmez. Bu, her ikisi de bir tür kitaplığı oluşturup kaydeden [Derleme Kayıt aracına (Regasm.exe)](regasm-exe-assembly-registration-tool.md)karşılık gelir. COM ile bir tür kitaplığı üretmek ve kaydetmek için, Regasm.exe'yi kullanın.  
  
 `/win32`Ya da `/win64` seçeneğini belirtmezseniz, Tlbexp.exe derlemeyi gerçekleştirdiğiniz bilgisayarın türüne karşılık gelen bir 32-bit veya 64 bit tür kitaplığı oluşturur (32 bit veya 64 bit bilgisayar). Çapraz derleme amacıyla, `/win64` 32 bitlik bir bilgisayarda seçeneğini kullanarak 64 bit tür kitaplığı oluşturabilir ve bir `/win32` 32-bit tür kitaplığı oluşturmak için 64-bit bir bilgisayarda seçeneğini kullanabilirsiniz. 32 bitlik tür kitaplıklarında, <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> değer olarak ayarlanır <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32> . 64 bitlik tür kitaplıklarında, <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> değer olarak ayarlanır <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64> . Tüm veri türü dönüşümleri (örneğin, ve gibi işaretçi ölçekli veri türleri `IntPtr` `UIntPtr` ) uygun şekilde dönüştürülür.  
  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>Veya değerini belirtmek için özniteliğini kullanırsanız <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> `VT_UNKOWN` `VT_DISPATCH` , Tlbexp.exe, alanın sonraki kullanımını yoksayar <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> . Örneğin, aşağıdaki imzalar verildiğinde:  
  
```csharp
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_UNKNOWN, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructUnkSafe(){return null;}  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_DISPATCH, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructDispSafe(){return null;}  
```  
  
 aşağıdaki tür kitaplığı oluşturulur:  
  
```cpp
[id(0x60020004)]  
HRESULT StructUnkSafe([out, retval] SAFEARRAY(IUnknown*)* pRetVal);  
[id(0x60020005)]  
HRESULT StructDispSafe([out, retval] SAFEARRAY(IDispatch*)* pRetVal);  
```  
  
 Tlbexp.exe alanı yok saymadığını unutmayın <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> .  
  
 Tür kitaplıkları derlemelerde bulunan tüm bilgileri barındıramayacağından, dışarı aktarma işlemi sırasında Tlbexp.exe bazı verileri atabilir. Dönüştürme işleminin açıklaması ve bir tür kitaplığına yayılan her bir bilgi parçasının kaynağının tanımlanması için bkz. [tür kitaplığı dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100)).  
  
 Tür kitaplığı verme programı, <xref:System.TypedReference> `VARIANT` nesne yönetilmeyen kodda anlamı olmasa bile, parametreleri olan yöntemleri dışarı <xref:System.TypedReference> aktardığından emin olmak için. Parametreleri olan yöntemleri dışarı aktardığınızda <xref:System.TypedReference> tür kitaplığı verme programı bir uyarı veya hata oluşturmaz ve elde edilen tür kitaplığını kullanan yönetilmeyen kod düzgün çalışmaz.  
  
 Tür Kitaplığı Verme Programı Microsoft Windows 2000 ve sonraki sürümlerde desteklenir.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, içinde bulunan derlemeyle aynı ada sahip bir tür kitaplığı oluşturur `myTest.dll` .  
  
```console  
tlbexp myTest.dll  
```  
  
 Aşağıdaki komut, adında bir tür kitaplığı oluşturur `clipper.tlb` .  
  
```console  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 Aşağıdaki örnekte, bir tür kitaplığını Tlbimp.exe kullanılarak içeri aktarılan derlemelere başvuran bir derlemeden dışarı aktarmak için Tlbexp.exe'nin kullanılması gösterilmektedir.  
  
 Önce tür kitaplığını içeri aktarmak `myLib.tlb` ve olarak kaydetmek için Tlbimp.exe kullanın `myLib.dll` .  
  
```console  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 Aşağıdaki komut, `Sample.dll,` Önceki örnekte oluşturulan başvuruları derlemek Için C# derleyicisini kullanır `myLib.dll` .  
  
```console  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 Aşağıdaki komut, bu başvurular için bir tür kitaplığı oluşturur `Sample.dll` `myLib.dll` .  
  
```console  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.TypeLibExporterFlags>
- [Araçlar](index.md)
- [Regasm.exe (derleme kayıt aracı)](regasm-exe-assembly-registration-tool.md)
- [Derlemeden tür kitaplığına dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))
- [Tlbimp.exe (tür kitaplığı Içeri Aktarıcı)](tlbimp-exe-type-library-importer.md)
- [Komut Istemleri](developer-command-prompt-for-vs.md)
