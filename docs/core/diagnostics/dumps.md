---
title: Dökümler-.NET
description: .NET ' te döküme giriş.
ms.date: 10/12/2020
ms.openlocfilehash: 56cf4085d10658c828bac39be93eed3f774e00d5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242779"
---
# <a name="dumps"></a>Dökümleri

Döküm, oluşturulduğu sırada işlemin anlık görüntüsünü içeren ve uygulamanızın durumunu incelemek için yararlı olabilecek bir dosyadır. Dökümler, üretim veya CI ortamları gibi bir hata ayıklayıcı eklemek zor olduğunda .NET uygulamanızda hata ayıklamak için kullanılabilir. Dökümleri kullanmak, sorunlu işlemin durumunu yakalamanızı ve uygulamayı durdurmak zorunda kalmadan incelemenizi sağlar.

## <a name="collect-dumps"></a>Dökümleri topla

Dökümler, uygulamanızı çalıştırdığınız platforma bağlı olarak çeşitli yollarla toplanabilir.

> [!NOTE]
> Bir kapsayıcının içinde döküm toplama, veya aracılığıyla eklenebilen PTRACE özelliği gerektirir `--cap-add=SYS_PTRACE` `--privileged` .

> [!NOTE]
> Dökümler, çalışan işlemin tam belleğini içerebildiğinden gizli bilgiler içerebilir. Bunları herhangi bir güvenlik kısıtlaması ve gudances ile işleyin.

### <a name="collecting-dumps-on-crash"></a>Kilitlenme durumunda dökümleri toplama

Uygulamanızı kilitlenme sonrasında döküm toplayacak şekilde yapılandırmak için ortam değişkenlerini kullanabilirsiniz. Bu, neden çökme oluştuğunu anlamak istediğinizde yararlı olur. Örneğin, bir özel durum oluştuğunda döküm yakalama, kilitlendikçe uygulamanın durumunu inceleyerek bir sorunu belirlemenize yardımcı olur.

Aşağıdaki tabloda, kilitlenme üzerinde dökümleri toplamak için yapılandırabileceğiniz ortam değişkenleri gösterilmektedir.

|Ortam değişkeni|Açıklama|Varsayılan değer|
|-------|---------|---|
|`COMPlus_DbgEnableMiniDump`|1 olarak ayarlanırsa, temel döküm oluşturmayı etkinleştirin.|0|
|`COMPlus_DbgMiniDumpType`|Toplanacak döküm türü. Daha fazla bilgi için aşağıdaki tabloya bakın|2 ( `MiniDumpWithPrivateReadWriteMemory` )|
|`COMPlus_DbgMiniDumpName`|Döküm yazılacak dosyanın yolu.|`/tmp/coredump.<pid>`|
|`COMPlus_CreateDumpDiagnostics`|1 olarak ayarlanırsa, döküm işleminin tanılama günlüğünü etkinleştirin.|0|

Aşağıdaki tabloda, için, `COMPlus_DbgMiniDumpType` bir değer olarak belirtime için kullanabileceğiniz tüm seçenekler gösterilmektedir. Örneğin, `COMPlus_DbgMiniDumpType` 1 olarak ayarlandığında, `MiniDumpNormal` kilitlenme üzerinde tür dökümü toplanacaktır.

|Değer|Adı|Açıklama|
|-----|----|-----------|
|1|`MiniDumpNormal`|Yalnızca bir işlemdeki mevcut tüm iş parçacıkları için yığın izlemelerini yakalamak için gereken bilgileri ekleyin. Sınırlı GC yığın belleği ve bilgileri.|
|2|`MiniDumpWithPrivateReadWriteMemory`|Bir işlemdeki tüm mevcut iş parçacıkları için yığın izlemelerini yakalamak için gereken GC yığınlarını ve bilgileri içerir.|
|3|`MiniDumpFilterTriage`|Yalnızca bir işlemdeki mevcut tüm iş parçacıkları için yığın izlemelerini yakalamak için gereken bilgileri ekleyin. Sınırlı GC yığın belleği ve bilgileri.|
|4|`MiniDumpWithFullMemory`|İşlemdeki tüm erişilebilir belleği dahil edin. Ham bellek verileri sonuna dahildir, böylece ilk yapılar ham bellek bilgileri olmadan doğrudan eşleştirilebilir. Bu seçenek çok büyük bir dosyanın oluşmasına neden olabilir.|

### <a name="collecting-dumps-at-specific-point-in-time"></a>Belirli bir zaman noktasında dökümleri toplama

Uygulama henüz kilitlenmemişse bir döküm toplamak isteyebilirsiniz. Örneğin, bir kilitlenmeyle gibi görünen bir uygulamanın durumunu incelemek isterseniz, uygulama hala çalıştığından, kilitlenme üzerinde dökümleri toplamak üzere ortam değişkenlerini yapılandırmak yararlı olmayacaktır.

Kendi isteğinizin dökümünü toplamak için, `dotnet-dump` dökümleri toplamak ve analiz etmek için BIR CLI aracı olan kullanabilirsiniz. İle dökümleri toplamak üzere kullanma hakkında daha fazla bilgi için `dotnet-dump` bkz. [döküm toplama ve analiz yardımcı programı](dotnet-dump.md).

## <a name="analyze-dumps"></a>Dökümleri çözümle

Dökümler kullanılarak analiz edilebilir [`dotnet-dump`](dotnet-dump.md) .

## <a name="see-also"></a>Ayrıca bkz.

.NET uygulamanızdaki sorunları tanılamanıza yardımcı olması için dökümleri nasıl kullanabileceğinizi öğrenin.

* [Linux dökümleri hata ayıklama](debug-linux-dumps.md) öğreticisinde, Linux 'ta toplanan bir dökümde hata ayıklama işlemi adım adım gösterilmektedir.

* [Hata ayıklama kilitlenmesi](debug-deadlock.md) öğreticisinde, dökümleri kullanarak .net uygulamanızda kilitlenmeyle hata ayıklama işlemi adım adım gösterilmektedir.
