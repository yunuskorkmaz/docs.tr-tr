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
ms.openlocfilehash: 1d2380ff607836b5dc15e7194b90dd3a53d1d2c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180267"
---
# <a name="tlbexpexe-type-library-exporter"></a>Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)
Tür Kitaplığı Verme Programı, bir ortak dil çalışma zamanı derlemesinde tanımlanan türleri açıklayan bir tür kitaplığı üretir.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
tlbexp assemblyName [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*Assemblyname*|Bir tür kitaplığının kendisi için dışarı aktarılacağı derleme.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/asmpath:** *dizin*|Derlemelerin aranacağı konumu belirtir. Bu seçeneği kullanırsanız, geçerli dizini de dahil olmak üzere, başvurulan derlemelerin aranacağı konumları açıkça belirtmeniz gerekir.<br /><br /> **Asmpath** seçeneğini kullandığınızda, Tür Kitaplığı İhracatçısı genel montaj önbelleğinde (GAC) bir derleme aramaz.|  
|**/yardım**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/names:** *dosya adı*|Bir tür kitaplığındaki adların büyük küçük harfle nasıl yazılacağını belirtir. *Dosya adı* bağımsız değişkeni bir metin dosyasıdır. Dosyadaki her bir satır, tür kitaplığındaki bir adın büyük küçük harfle nasıl yazılacağını belirtir.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/oldnames**|Bir tür adı çakışması varsa, Tlbexp.exe'yi donatılmış tür adlarını dışarı aktarmaya zorlar. .NET Framework sürüm 2.0'dan önceki sürümlerde varsayılan davranışın bu olduğunu unutmayın.|  
|**/out:** *dosya*|Üretilecek tür kitaplığı dosyasının adını belirtir. Bu seçeneği atlarsanız, Tlbexp.exe, derlemeyle (derlemeyi içeren dosyayla aynı olması gerekmeyen, gerçek derleme adı) aynı adda ve .tlb uzantılı bir tür kitaplığı üretir.|  
|**/sessizlik:**`warningnumber`|Belirtilen uyarının görüntülenmesini bastırır. Bu seçenek **/silent**ile kullanılamaz.|  
|**/silent**|Başarı iletilerinin görüntülenmesini bastırır. Bu seçenek **/silence**ile kullanılamaz.|  
|**/tlbreference:** *typelibrarynamename*|Tlbexp.exe'yi, kayıt defterine danışmadan tür kitaplığı başvurularını açıkça çözmeye zorlar. Örneğin, derleme B derleme A'ya başvurursa, kayıt defterinde belirtilen tür kitaplığına güvenmek yerine, bir açık tür kitaplığı başvurusu sağlamak için bu seçeneği kullanabilirsiniz. Tlbexp.exe, tür kitaplığı sürümünün derleme sürümüyle eşleşmesini sağlamak için bir sürüm denetimi yapar; tersi durumda, bir hata üretir.<br /><br /> **Tlbreference** seçeneğinin, özniteliğin <xref:System.Runtime.InteropServices.ComImportAttribute> başka bir tür tarafından uygulanan bir arabirime uygulandığı durumlarda kayıt defterine hala danışacağını unutmayın.|  
|**/tlbrefpath:** *yol*|Başvurulan tür kitaplığının tam olarak belirtilen yolu.|  
|**/win32**|64 bit'lik bir bilgisayarda derleme yaparken, bu seçenek Tlbexp.exe'nin bir 32 bit tür kitaplığı ürettiğini belirtir.|  
|**/win64**|32 bit bilgisayarda derlediğinizde, bu seçenek Tlbexp.exe'nin 64 bit türde bir kitaplık oluşturduğunu belirtir.|  
|**/ayrıntılı**|Ayrıntılı modu belirtir; kendileri için bir tür kitaplığı üretilmesi gereken tüm başvurulan derlemelerin listesini görüntüler.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
> Tlbexp.exe için komut satırı seçenekleri büyük-küçük harfe duyarlıdır ve herhangi bir sırada sağlanabilir. Tek yapmanız gereken, onu benzersiz şekilde tanımlamak için seçeneği yeterince belirtmektir. Örneğin, **/n** **/nologo**'ya eşdeğerdir ve **/o:** *outfile.tlb* **/out'** a eşdeğerdir: *outfile.tlb*.  
  
## <a name="remarks"></a>Açıklamalar  
 Tlbexp.exe, derlemede tanımlanan türlerin tanımlarını içeren bir tür kitaplığı üretir. Visual Basic 6.0 gibi uygulamalar, derlemede tanımlanan .NET türlerine bağlanacak üretilmiş tür kitaplığını kullanabilir.  
  
> [!IMPORTANT]
> Windows meta veri (.winmd) dosyalarını dışarı aktarmak için Tlbexp.exe'yi kullanamazsınız. Windows Çalışma Zamanı derlemelerinin dışarı aktarılması desteklenmez.  
  
 Tüm derleme bir kez dönüştürülür. Derlemede tanımlanan türlerin bir alt kümesi için tür bilgisi üretmek üzere Tlbexp.exe'yi kullanamazsınız.  
  
 [Tür Kitaplığı İthalatçısı (Tlbimp.exe)](tlbimp-exe-type-library-importer.md)kullanılarak alınan bir derlemeden tür kitaplığı üretmek için Tlbexp.exe'yi kullanamazsınız. Onun yerine, Tlbimp.exe ile içeri aktarılan özgün tür kitaplığına başvurmanız gerekir. Tlbimp.exe kullanılarak içeri aktarılan derlemelere başvuran bir derlemeden bir tür kitaplığını içeri aktarabilirsiniz. Aşağıdaki örnekler bölümüne bakın.  
  
 Tlbexp.exe, üretilen tür kitaplıklarını geçerli çalışma dizinine veya çıktı dosyası için belirtilen dizine yerleştirir. Tek bir derleme, birçok tür kitaplığının üretilmesine neden olabilir.  
  
 Tlbexp.exe bir tür kitaplığı oluşturur ama bunu kaydetmez. Bu, bir tür kitaplığını oluşturan ve kaydeden [Montaj Kayıt aracının (Regasm.exe)](regasm-exe-assembly-registration-tool.md)aksinedir. COM ile bir tür kitaplığı üretmek ve kaydetmek için, Regasm.exe'yi kullanın.  
  
 `/win32` Tlbexp.exe, derlemeyi gerçekleştirdiğiniz bilgisayar türüne (32 bit veya 64 bit bilgisayar) karşılık gelen 32 bit veya 64 bit türünde bir kitaplık `/win64` oluşturur. Çapraz derleme amacıyla, 32 bit `/win64` lik bir bilgisayardaki seçeneği kullanarak 64 bit türde bir `/win32` kitaplık oluşturabilir ve 64 bit lik bir bilgisayardaki seçeneği kullanarak 32 bit türde bir kitaplık oluşturabilirsiniz. 32 bit türü kitaplıklarda <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> değer <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>. 64 bit türü kitaplıklarda <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> değer <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>. Tüm veri türü dönüşümleri (örneğin, işaretçi `IntPtr` boyutunda veri türleri gibi) `UIntPtr`uygun şekilde dönüştürülür.  
  
 Bir değer <xref:System.Runtime.InteropServices.MarshalAsAttribute> belirtmek için <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> özniteliği `VT_UNKOWN` kullanırsanız veya `VT_DISPATCH`, Tlbexp.exe <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> alanın sonraki herhangi bir kullanımını yok sayar. Örneğin, aşağıdaki imzalar verildiğinde:  
  
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
  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> Tlbexp.exe'nin alanı yok saydığını unutmayın.  
  
 Tür kitaplıkları derlemelerde bulunan tüm bilgileri barındıramayacağından, dışarı aktarma işlemi sırasında Tlbexp.exe bazı verileri atabilir. Dönüşüm sürecinin açıklanması ve bir tür kitaplığına yayılan her bir bilgi parçasının kaynağının tanımlanması [için, Derleme'den Tür Kitaplığı Dönüşüm Özeti'ne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))bakın.  
  
 Tür Kitaplığı <xref:System.TypedReference> `VARIANT`İhracatçısı, nesnenin <xref:System.TypedReference> yönetilmeyen kodda bir anlamı olmamasına rağmen parametreleri olan yöntemleri dışa aktarmaz. Parametreleri olan <xref:System.TypedReference> yöntemleri dışa aktardığınızda, Tür Kitaplığı İhracatçısı bir uyarı veya hata oluşturmaz ve ortaya çıkan tür kitaplığını kullanan yönetilmeyen kod düzgün çalışmaz.  
  
 Tür Kitaplığı Verme Programı Microsoft Windows 2000 ve sonraki sürümlerde desteklenir.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, 'de `myTest.dll`bulunan derlemeyle aynı ada sahip bir tür kitaplığı oluşturur.  
  
```console  
tlbexp myTest.dll  
```  
  
 Aşağıdaki komut, adı `clipper.tlb`olan bir tür kitaplığı oluşturur.  
  
```console  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 Aşağıdaki örnekte, bir tür kitaplığını Tlbimp.exe kullanılarak içeri aktarılan derlemelere başvuran bir derlemeden dışarı aktarmak için Tlbexp.exe'nin kullanılması gösterilmektedir.  
  
 Önce tlbimp.exe türü kitaplığı `myLib.tlb` almak ve `myLib.dll`olarak kaydetmek için kullanın .  
  
```console  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 Aşağıdaki komut, önceki örnekte oluşturulan başvuruları `Sample.dll,` `myLib.dll` derlemek için C# derleyicisini kullanır.  
  
```console  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 Aşağıdaki komut, bu başvurular `Sample.dll` `myLib.dll`için bir tür kitaplığı oluşturur.  
  
```console  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.TypeLibExporterFlags>
- [Araçlar](index.md)
- [Regasm.exe (Derleme Kayıt Aracı)](regasm-exe-assembly-registration-tool.md)
- [Derleme den Türe Dönüşüm Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))
- [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](tlbimp-exe-type-library-importer.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
