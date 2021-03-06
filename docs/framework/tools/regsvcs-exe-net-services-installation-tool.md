---
title: Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)
description: .NET Hizmetleri Yükleme Aracı Regsvcs.exe kullanın. Bir derlemeyi yükleyin ve kaydedin, bir sınıfa programlı olarak eklediğiniz hizmetleri yapılandırın ve daha fazlasını yapın.
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: a989ddf8b14806879917e4078f60486f225b00e3
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259209"
---
# <a name="regsvcsexe-net-services-installation-tool"></a>Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)

.NET Hizmetleri Yükleme aracı aşağıdaki eylemleri gerçekleştirir:  
  
- Bir derlemeyi yükler ve kaydeder.  
  
- Bir tür kitaplığı üretir, kaydeder ve belirtilen bir COM+ uygulamasına yükler.  
  
- Sınıfınıza program aracılığıyla eklediğiniz hizmetleri yapılandırır.  
  
 Aracı çalıştırmak için, [geliştiriciler için bir komut satırı kabuğu](/visualstudio/ide/reference/command-prompt-powershell)kullanın.  
  
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
|*assemblyFile.dll*|Kaynak derleme dosyası. Derlemenin tanımlayıcı ad ile imzalanması gerekir. Daha fazla bilgi için bkz. [bir derlemeyi güçlü bir adla imzalama](../../standard/assembly/sign-strong-name.md).|  
  
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
|**/reconfig**|Varolan bir hedef uygulamayı yeniden yapılandırır. Bu varsayılan seçenektir.|  
|**/tlb:** *TypeLibraryFile*|Yüklenecek tür kitaplığı dosyasını belirtir.|  
|**p**|Hedef uygulamayı kaldırır.|  
|**/**|Sessiz modu belirtir; logo ve başarı iletisi görüntüsünü bastırır.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  

 Regsvcs.exe, *assemblyFile.dll* tarafından belirtilen bir kaynak derleme dosyası gerektirir. Bu derlemenin tanımlayıcı ad ile imzalanması gerekir. Tanımlayıcı ad imzalama hakkında daha fazla bilgi için bkz. [bir derlemeyi tanımlayıcı bir adla imzalama](../../standard/assembly/sign-strong-name.md). Hedef uygulamanın ve tür kitaplığı dosyasının adları isteğe bağlıdır. *ApplicationName* bağımsız değişkeni kaynak derleme dosyasından oluşturulabilir ve henüz yoksa Regsvcs.exe tarafından oluşturulur. *TypeLibraryFile* bağımsız değişkeni bir tür kitaplığı adı belirtebilir. Bir tür kitaplığı adı belirtmezseniz, Regsvcs.exe derleme adını varsayılan olarak kullanır.  
  
 Regsvcs.exe bir bileşenin yöntemlerini kaydettiğinde, bu yöntemler için [talepler](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) ve [bağlantı taleplerine](../misc/link-demands.md) tabidir. Araç tam olarak güvenilen bir ortamda yürütüldüğünden, izin taleplerinin çoğu başarılı olur. Ancak Regsvcs.exe, veya için talep veya bağlantı talebi tarafından korunan yöntemlerle bileşenleri kaydedemez <xref:System.Security.Permissions.StrongNameIdentityPermission> <xref:System.Security.Permissions.PublisherIdentityPermission> .  
  
 Regsvcs.exe'yi kullanmak için yerel bilgisayarda yönetici ayrıcalıklarına sahip olmanız gerekir.  
  
 Bu eylemlerden herhangi birini gerçekleştirirken Regsvcs.exe başarısız olursa, ilgili hata iletilerini görüntüler.  
  
## <a name="examples"></a>Örnekler  

 Aşağıdaki komut ' de bulunan tüm ortak sınıfları `myTest.dll` `myTargetApp` (var olan bir com+ uygulaması) öğesine ekler ve `myTest.tlb` tür kitaplığını üretir.  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 Aşağıdaki komut ' de bulunan tüm ortak sınıfları `myTest.dll` `myTargetApp` (var olan bir com+ uygulaması) öğesine ekler ve `newTest.tlb` tür kitaplığını üretir.  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama](../../standard/assembly/sign-strong-name.md)
- [Geliştirici komut satırı kabukları](/visualstudio/ide/reference/command-prompt-powershell)
