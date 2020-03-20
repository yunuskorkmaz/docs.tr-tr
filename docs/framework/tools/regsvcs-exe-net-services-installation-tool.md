---
title: Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: aecd2f6894558b45898c7f22dd333617d9e2e327
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180355"
---
# <a name="regsvcsexe-net-services-installation-tool"></a>Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)
.NET Hizmetleri Yükleme aracı aşağıdaki eylemleri gerçekleştirir:  
  
- Bir derlemeyi yükler ve kaydeder.  
  
- Bir tür kitaplığı üretir, kaydeder ve belirtilen bir COM+ uygulamasına yükler.  
  
- Sınıfınıza program aracılığıyla eklediğiniz hizmetleri yapılandırır.  
  
 To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*assemblyFile.dll*|Kaynak derleme dosyası. Derlemenin tanımlayıcı ad ile imzalanması gerekir. Daha fazla bilgi için [bkz.](../../standard/assembly/sign-strong-name.md)|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/appdir:** *yol*|Uygulamanın kök dizinini belirtir.|  
|**/appname:** *applicationName*|Bulunacak veya oluşturulacak COM+ uygulamasının adını belirtir.|  
|**/c**|Hedef uygulamayı oluşturur.|  
|**/componly**|Yalnızca bileşenleri yapılandırır; yöntemleri ve arabirimleri yoksayar.|  
|**/exapp**|Varolan bir uygulamayı beklemek üzere aracı belirtir.|  
|**/extlb**|Varolan bir tür kitaplığını kullanır.|  
|**/fc**|Hedef uygulamayı bulur veya oluşturur.|  
|**/yardım**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/noreconfig**|Varolan bir hedef uygulamayı yeniden yapılandırmaz.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/parname:** *isim*|Bulunacak veya oluşturulacak COM+ uygulamasının adını veya kimliğini belirtir.|  
|**/reconfig**|Varolan bir hedef uygulamayı yeniden yapılandırır. Bu varsayılandır.|  
|**/tlb:** *typelibraryfile*|Yüklenecek tür kitaplığı dosyasını belirtir.|  
|**/u**|Hedef uygulamayı kaldırır.|  
|**/sessiz**|Sessiz modu belirtir; logo ve başarı iletisi görüntüsünü bastırır.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Regsvcs.exe *assemblyFile.dll*tarafından belirtilen bir kaynak derleme dosyası gerektirir. Bu derlemenin tanımlayıcı ad ile imzalanması gerekir. Güçlü ad imzalama hakkında daha fazla bilgi için [bkz.](../../standard/assembly/sign-strong-name.md) Hedef uygulamanın ve tür kitaplığı dosyasının adları isteğe bağlıdır. *ApplicationName* bağımsız değişkeni kaynak derleme dosyasından oluşturulabilir ve zaten yoksa Regsvcs.exe tarafından oluşturulur. *Typelibraryfile* bağımsız değişkeni bir tür kitaplığı adı belirtebilir. Bir tür kitaplığı adı belirtmezseniz, Regsvcs.exe derleme adını varsayılan olarak kullanır.  
  
 Regsvcs.exe bir bileşenin yöntemlerini kaydettiğinde, bu yöntemlerle ilgili [taleplere](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) ve [bağlantı taleplerine](../misc/link-demands.md) tabidir. Araç tam olarak güvenilen bir ortamda yürütüldüğünden, izin taleplerinin çoğu başarılı olur. Ancak, Regsvcs.exe bileşenleri bir talep veya bağlantı talebi <xref:System.Security.Permissions.StrongNameIdentityPermission> tarafından <xref:System.Security.Permissions.PublisherIdentityPermission>korunan yöntemlerle kaydedemez.  
  
 Regsvcs.exe'yi kullanmak için yerel bilgisayarda yönetici ayrıcalıklarına sahip olmanız gerekir.  
  
 Bu eylemlerden herhangi birini gerçekleştirirken Regsvcs.exe başarısız olursa, ilgili hata iletilerini görüntüler.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, içerdiği `myTest.dll` tüm ortak `myTargetApp` sınıfları (varolan bir `myTest.tlb` COM+ uygulamasına) ekler ve tür kitaplığını üretir.  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 Aşağıdaki komut, içerdiği `myTest.dll` tüm ortak `myTargetApp` sınıfları (varolan bir `newTest.tlb` COM+ uygulamasına) ekler ve tür kitaplığını üretir.  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama](../../standard/assembly/sign-strong-name.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
