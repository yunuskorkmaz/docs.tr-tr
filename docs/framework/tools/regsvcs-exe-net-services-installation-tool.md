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
ms.openlocfilehash: 1af93ae89d027bccdd52b9cd9c49f8e620303677
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104936"
---
# <a name="regsvcsexe-net-services-installation-tool"></a>Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)
.NET Hizmetleri Yükleme aracı aşağıdaki eylemleri gerçekleştirir:  
  
- Bir derlemeyi yükler ve kaydeder.  
  
- Bir tür kitaplığı üretir, kaydeder ve belirtilen bir COM+ uygulamasına yükler.  
  
- Sınıfınıza program aracılığıyla eklediğiniz hizmetleri yapılandırır.  
  
 Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
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
|*assemblyFile. dll*|Kaynak derleme dosyası. Derlemenin tanımlayıcı ad ile imzalanması gerekir. Daha fazla bilgi için bkz. [bir derlemeyi güçlü bir adla imzalama](../../standard/assembly/sign-strong-name.md).|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Appdir:** *yol*|Uygulamanın kök dizinini belirtir.|  
|**/appname:** *ApplicationName*|Bulunacak veya oluşturulacak COM+ uygulamasının adını belirtir.|  
|**/c**|Hedef uygulamayı oluşturur.|  
|**/componly**|Yalnızca bileşenleri yapılandırır; yöntemleri ve arabirimleri yoksayar.|  
|**/exapp**|Varolan bir uygulamayı beklemek üzere aracı belirtir.|  
|**/extlb**|Varolan bir tür kitaplığını kullanır.|  
|**/FC**|Hedef uygulamayı bulur veya oluşturur.|  
|**/Help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/noreconfig**|Varolan bir hedef uygulamayı yeniden yapılandırmaz.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/parName:** *ad*|Bulunacak veya oluşturulacak COM+ uygulamasının adını veya kimliğini belirtir.|  
|**/reconfig**|Varolan bir hedef uygulamayı yeniden yapılandırır. Bu varsayılandır.|  
|**/tlb:** *TypeLibraryFile*|Yüklenecek tür kitaplığı dosyasını belirtir.|  
|**p**|Hedef uygulamayı kaldırır.|  
|**/quiet**|Sessiz modu belirtir; logo ve başarı iletisi görüntüsünü bastırır.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 RegSvcs. exe, *assemblyFile. dll*tarafından belirtilen bir kaynak derleme dosyası gerektirir. Bu derlemenin tanımlayıcı ad ile imzalanması gerekir. Tanımlayıcı ad imzalama hakkında daha fazla bilgi için bkz. [bir derlemeyi tanımlayıcı bir adla imzalama](../../standard/assembly/sign-strong-name.md). Hedef uygulamanın ve tür kitaplığı dosyasının adları isteğe bağlıdır. *ApplicationName* bağımsız değişkeni kaynak derleme dosyasından oluşturulabilir ve henüz yoksa RegSvcs. exe tarafından oluşturulacaktır. *TypeLibraryFile* bağımsız değişkeni bir tür kitaplığı adı belirtebilir. Bir tür kitaplığı adı belirtmezseniz, Regsvcs.exe derleme adını varsayılan olarak kullanır.  
  
 RegSvcs. exe bir bileşenin yöntemlerini kaydettiğinde, bu yöntemler için [talepler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) ve [bağlantı taleplerine](../misc/link-demands.md) tabidir. Araç tam olarak güvenilen bir ortamda yürütüldüğünden, izin taleplerinin çoğu başarılı olur. Ancak, RegSvcs. exe, <xref:System.Security.Permissions.StrongNameIdentityPermission> veya <xref:System.Security.Permissions.PublisherIdentityPermission>için talep veya bağlantı talebi tarafından korunan yöntemlerle bileşenleri kaydedemez.  
  
 Regsvcs.exe'yi kullanmak için yerel bilgisayarda yönetici ayrıcalıklarına sahip olmanız gerekir.  
  
 Bu eylemlerden herhangi birini gerçekleştirirken Regsvcs.exe başarısız olursa, ilgili hata iletilerini görüntüler.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, `myTest.dll` bulunan tüm ortak sınıfları `myTargetApp` (var olan bir COM+ uygulaması) öğesine ekler ve `myTest.tlb` tür kitaplığı oluşturur.  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 Aşağıdaki komut, `myTest.dll` bulunan tüm ortak sınıfları `myTargetApp` (var olan bir COM+ uygulaması) öğesine ekler ve `newTest.tlb` tür kitaplığı oluşturur.  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama](../../standard/assembly/sign-strong-name.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
