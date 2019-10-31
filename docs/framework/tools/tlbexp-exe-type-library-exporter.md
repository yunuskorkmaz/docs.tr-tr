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
ms.openlocfilehash: f421a9865e457a4e8e08644671efb55c731db28b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104339"
---
# <a name="tlbexpexe-type-library-exporter"></a>Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)
Tür Kitaplığı Verme Programı, bir ortak dil çalışma zamanı derlemesinde tanımlanan türleri açıklayan bir tür kitaplığı üretir.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
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
|**/sessizlik:** `warningnumber`|Belirtilen uyarının görüntülenmesini bastırır. Bu seçenek **/Silent**ile kullanılamaz.|  
|**/silent**|Başarı iletilerinin görüntülenmesini bastırır. Bu seçenek **/sessizlik**ile kullanılamaz.|  
|**/tlbreference:** *TypeLibraryName*|Tlbexp.exe'yi, kayıt defterine danışmadan tür kitaplığı başvurularını açıkça çözmeye zorlar. Örneğin, derleme B derleme A'ya başvurursa, kayıt defterinde belirtilen tür kitaplığına güvenmek yerine, bir açık tür kitaplığı başvurusu sağlamak için bu seçeneği kullanabilirsiniz. Tlbexp.exe, tür kitaplığı sürümünün derleme sürümüyle eşleşmesini sağlamak için bir sürüm denetimi yapar; tersi durumda, bir hata üretir.<br /><br /> **Tlbreference** seçeneğinin, <xref:System.Runtime.InteropServices.ComImportAttribute> özniteliğinin daha sonra başka bir tür tarafından uygulanan bir arabirime uygulandığı durumlarda kayıt defterine hala başvurabileceğini unutmayın.|  
|**/tlbrefpath:** *yol*|Başvurulan tür kitaplığının tam olarak belirtilen yolu.|  
|**/Win32**|64 bit'lik bir bilgisayarda derleme yaparken, bu seçenek Tlbexp.exe'nin bir 32 bit tür kitaplığı ürettiğini belirtir.|  
|**/Win64**|32 bitlik bir bilgisayarda derlerken, bu seçenek Tlbexp. exe ' nin 64 bit tür kitaplığı üretmediğini belirtir.|  
|**/verbose**|Ayrıntılı modu belirtir; kendileri için bir tür kitaplığı üretilmesi gereken tüm başvurulan derlemelerin listesini görüntüler.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
> Tlbexp.exe için komut satırı seçenekleri büyük-küçük harfe duyarlıdır ve herhangi bir sırada sağlanabilir. Tek yapmanız gereken, onu benzersiz şekilde tanımlamak için seçeneği yeterince belirtmektir. Örneğin, **/n** **/nologo**ile eşdeğerdir ve **/o:** *çıkışdosyası. tlb* , **/Out:** *çıkışdosyası. tlb*ile eşdeğerdir.  
  
## <a name="remarks"></a>Açıklamalar  
 Tlbexp.exe, derlemede tanımlanan türlerin tanımlarını içeren bir tür kitaplığı üretir. Visual Basic 6.0 gibi uygulamalar, derlemede tanımlanan .NET türlerine bağlanacak üretilmiş tür kitaplığını kullanabilir.  
  
> [!IMPORTANT]
> Windows meta veri (.winmd) dosyalarını dışarı aktarmak için Tlbexp.exe'yi kullanamazsınız. Windows Çalışma Zamanı derlemelerinin dışarı aktarılması desteklenmez.  
  
 Tüm derleme bir kez dönüştürülür. Derlemede tanımlanan türlerin bir alt kümesi için tür bilgisi üretmek üzere Tlbexp.exe'yi kullanamazsınız.  
  
 [Tür kitaplığı alma programı (Tlbimp. exe)](tlbimp-exe-type-library-importer.md)kullanılarak içeri aktarılan bir derlemeden bir tür kitaplığı oluşturmak Için Tlbexp. exe ' yi kullanamazsınız. Onun yerine, Tlbimp.exe ile içeri aktarılan özgün tür kitaplığına başvurmanız gerekir. Tlbimp.exe kullanılarak içeri aktarılan derlemelere başvuran bir derlemeden bir tür kitaplığını içeri aktarabilirsiniz. Aşağıdaki örnekler bölümüne bakın.  
  
 Tlbexp.exe, üretilen tür kitaplıklarını geçerli çalışma dizinine veya çıktı dosyası için belirtilen dizine yerleştirir. Tek bir derleme, birçok tür kitaplığının üretilmesine neden olabilir.  
  
 Tlbexp.exe bir tür kitaplığı oluşturur ama bunu kaydetmez. Bu, her ikisi de bir tür kitaplığı oluşturup kaydeden [Derleme Kayıt aracına (Regasm. exe)](regasm-exe-assembly-registration-tool.md)karşılık gelir. COM ile bir tür kitaplığı üretmek ve kaydetmek için, Regasm.exe'yi kullanın.  
  
 `/win32` veya `/win64` seçeneğini belirtmezseniz, Tlbexp. exe, derlemeyi gerçekleştirdiğiniz bilgisayarın türüne karşılık gelen bir 32-bit veya 64 bit tür kitaplığı oluşturur (32-bit veya 64-bit bilgisayar). Çapraz derleme amacıyla, 32 bitlik bir bilgisayardaki `/win64` seçeneğini kullanarak 64 bitlik bir tür kitaplığı oluşturabilir ve bir 32-bit tür kitaplığı oluşturmak için 64 bit bilgisayardaki `/win32` seçeneğini kullanabilirsiniz. 32 bitlik tür kitaplıklarında <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> değeri <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>olarak ayarlanır. 64 bitlik tür kitaplıklarında <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> değeri <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>olarak ayarlanır. Tüm veri türü dönüşümleri (örneğin, `IntPtr` ve `UIntPtr`gibi işaretçi ölçekli veri türleri) uygun şekilde dönüştürülür.  
  
 `VT_UNKOWN` veya `VT_DISPATCH`<xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> değerini belirtmek için <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliğini kullanırsanız, Tlbexp. exe, <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> alanının sonraki kullanımını yoksayar. Örneğin, aşağıdaki imzalar verildiğinde:  
  
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
  
 Tlbexp. exe ' nin <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> alanı yok saymadığını unutmayın.  
  
 Tür kitaplıkları derlemelerde bulunan tüm bilgileri barındıramayacağından, dışarı aktarma işlemi sırasında Tlbexp.exe bazı verileri atabilir. Dönüştürme işleminin açıklaması ve bir tür kitaplığına yayılan her bir bilgi parçasının kaynağının tanımlanması için bkz. [tür kitaplığı dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100)).  
  
 Tür kitaplığı verme programı, <xref:System.TypedReference> nesnesinin yönetilmeyen kodda anlamı olmasa bile, `VARIANT`<xref:System.TypedReference> parametrelere sahip yöntemleri dışarı aktardığına göz önünde koyulur. <xref:System.TypedReference> parametrelere sahip yöntemleri dışarı aktardığınızda tür kitaplığı verme programı bir uyarı veya hata oluşturmaz ve elde edilen tür kitaplığını kullanan yönetilmeyen kod düzgün çalışmaz.  
  
 Tür Kitaplığı Verme Programı Microsoft Windows 2000 ve sonraki sürümlerde desteklenir.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, `myTest.dll`bulunan derlemeyle aynı ada sahip bir tür kitaplığı oluşturur.  
  
```console  
tlbexp myTest.dll  
```  
  
 Aşağıdaki komut `clipper.tlb`adında bir tür kitaplığı oluşturur.  
  
```console  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 Aşağıdaki örnekte, bir tür kitaplığını Tlbimp.exe kullanılarak içeri aktarılan derlemelere başvuran bir derlemeden dışarı aktarmak için Tlbexp.exe'nin kullanılması gösterilmektedir.  
  
 Önce, tür kitaplığı `myLib.tlb` içeri aktarmak ve `myLib.dll`olarak kaydetmek için Tlbimp. exe ' yi kullanın.  
  
```console  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 Aşağıdaki komut, önceki örnekte C# oluşturulan `myLib.dll` başvuran `Sample.dll,` derlemek için derleyicisini kullanır.  
  
```console  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 Aşağıdaki komut, `myLib.dll`başvuran `Sample.dll` için bir tür kitaplığı oluşturur.  
  
```console  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.TypeLibExporterFlags>
- [Araçlar](index.md)
- [Regasm.exe (Derleme Kayıt Aracı)](regasm-exe-assembly-registration-tool.md)
- [Derlemeden tür kitaplığına dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))
- [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](tlbimp-exe-type-library-importer.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
