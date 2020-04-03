---
title: Regasm.exe (Derleme Kayıt Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Assembly Registration tool
- assemblies [.NET Framework], registering
- Regasm.exe
- registering assemblies
ms.assetid: e190e342-36ef-4651-a0b4-0e8c2c0281cb
ms.openlocfilehash: 5eeed43f3d60bd5e443226a16963557546d81e7c
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635412"
---
# <a name="regasmexe-assembly-registration-tool"></a>Regasm.exe (Derleme Kayıt Aracı)

Derleme Kayıt aracı, derleme içindeki meta verileri okur ve kayıt defterine gerekli girişleri ekler, bu da COM istemcilerinin şeffaf olarak .NET Framework sınıfları oluşturmalarına izin verir. Sınıf kaydettirildikten sonra, COM istemcileri artık sınıfı bir COM sınıfıymış gibi kullanabilir. Sınıf yalnızca bir defa, derleme yüklenirken kaydettirilir. Derleme içindeki sınıf örnekleri gerçekten kaydettirilene kadar COM'dan oluşturulamaz.

Aracı çalıştırmak için Visual Studio için Geliştirici Komut Komut Ustem'ini kullanın. Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
regasm assemblyFile [options]
```

## <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|*Assemblyfile*|COM ile kaydettirilecek derleme.|

|Seçenek|Açıklama|
|------------|-----------------|
|**/codebase**|Kayıt defterinde bir Kod Temeli girişi oluşturur. Codebase girişi, genel derleme önbelleğinde yüklü olmayan bir derlemeiçin dosya yolunu belirtir. Daha sonra kaydettiğiniz derlemeyi genel derleme önbelleğine yüklerseniz bu seçeneği belirtmeyin. **/codebase** seçeneğiyle belirttiğiniz *assemblyFile* bağımsız değişkeni [güçlü adlandırılmış](../../standard/assembly/strong-named.md)bir derleme olmalıdır.|
|**/kayıtlı**|Bu aracın yalnızca zaten kayıtlı durumdaki tür kitaplıklarına başvuracağını belirtir.|
|**/asmpath:dizin**|Derleme başvuruları içeren bir dizini belirtir. **/regfile** seçeneği ile kullanılmalıdır.|
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|
|**/regfile** [**:** *regFile*]|Gerekli kayıt defteri girdilerini içeren derleme için belirtilen .reg dosyasını oluşturur. Bu seçeneği belirtmek kayıt defterini değiştirmez. Bu seçeneği **/u** veya **/tlb** seçenekleriyle kullanamazsınız.|
|**/sessiz** veya **/s**|Başarı iletilerinin görüntülenmesini bastırır.|
|**/tlb** [**:** *typeLibFile*]|Belirtilen derlemeden, derleme içinde tanımlanmış erişilebilir türlerin tanımlarını içeren bir tür kitaplığı oluşturur.|
|**/kayıt dışı** veya **/u**|*AssemblyFile'da*bulunan gıyabılaş sınıflarının kaydını açar. Bu seçeneği kullanmamak, Regasm.exe'nin derlemedeki oluşturulabilir sınıfları kaydettirmesine neden olur.|
|**/ayrıntılı**|Ayrıntılı modu belirtir; **/tlb** seçeneğiyle belirtildiğinde, tür kitaplığı oluşturulması gereken başvurulan derlemelerin listesini görüntüler.|
|**/?** veya **/yardım**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

> [!NOTE]
> Regasm.exe komut satırı seçenekleri büyük/küçük harfe duyarsızdır. Seçeneğin, yalnızca onu benzersiz şekilde tanımlamaya yetecek kadarını sağlamanız yeterlidir. Örneğin, **/n** **/nologo** ve **/t'ye eşdeğerdir:** *outfile.tlb* **/tlb'ye eşdeğerdir:** *outfile.tlb*.

## <a name="remarks"></a>Açıklamalar

Değişiklikleri doğrudan kayıt defterine yapmak yerine kayıt defteri girişlerini içeren bir .reg dosyası oluşturmak için **/regfile** seçeneğini kullanabilirsiniz. Kayıt Defteri Düzenleyicisi (Regedit.exe) aracı ile .reg dosyasını içe aktararak, bir bilgisayarda kayıt defterini güncelleştirebilirsiniz. .reg dosyası, kullanıcı tanımlı kayıt işlevleri tarafından yapIlebilen kayıt defteri güncelleştirmeleri içermez. **/regfile** seçeneği yalnızca yönetilen sınıflar için kayıt defteri girişleri yayır. Bu seçenek, s veya `TypeLibID` `InterfaceID`s için girişler yaramaz.

**/tlb** seçeneğini belirttiğiniz zaman, Regasm.exe derlemede bulunan türleri açıklayan bir tür kitaplığı oluşturur ve kaydeder. RegAsm.exe oluşturulan tür kitaplıklarını geçerli çalışma dizinine veya çıktı dosyası için belirtilen dizine yerleştirir. Diğer derlemelere başvuran bir derleme için tür kitaplığı oluşturmak, bazı tür kitaplıklarının tek seferde oluşturulmasına neden olabilir. Tür kitaplığını Visual Studio gibi geliştirme araçlarına tür bilgileri sağlamak için kullanabilirsiniz. Kayıt yaptığınız derleme Tip Kitaplığı İthalatçısı ([Tlbimp.exe)](tlbimp-exe-type-library-importer.md)tarafından üretiliyorsa **/tlb** seçeneğini kullanmayın. Bir tür kitaplığından içeri aktarılmış bir derlemeden bir tür kitaplığını dışarı aktaramazsınız. **/tlb** seçeneğinin kullanılması, Tlbexp.exe'nin ürettiği tür kitaplığını kaydetmemesi dışında Tip Kitaplığı İhracatçısı ([Tlbexp.exe](tlbexp-exe-type-library-exporter.md)) ve Regasm.exe'yi kullanmakla aynı etkiye sahiptir.  Tür kitaplığını kaydetmek için **/tlb** seçeneğini kullanıyorsanız, tür kitaplığını n **/unregister** seçeneğiyle **birlikte /tlb** seçeneğini kullanabilirsiniz. İki seçeneği birlikte kullandığınızda tür kitaplığının ve arabirim girdilerinin kaydını kaldırırsınız, bu da kayıt defterini önemli ölçüde temizleyebilir.

Bir derlemeyi COM tarafından kullanılması için kaydettirdiğinize, Regasm.exe girdileri yerel bilgisayardaki kayıt defterine ekler. Daha ayrıntılı şekilde söylemek gerekirse, aynı derlemenin birden fazla sürümünün bir bilgisayarda yan yana çalışmasına olanak veren sürüme bağlı kayıt defteri anahtarları oluşturur. Bir derleme ilk kez kaydolduğunda, derleme için bir üst düzey anahtar oluşturulur ve belirli sürüm için benzersiz bir alt anahtar oluşturulur. Derlemenin yeni bir sürümünü her kaydettirdiğinizde, Regasm.exe yeni sürüm için bir alt anahtar oluşturur.

Örneğin, COM tarafından kullanılmak üzere yönetilen bileşen myComp.dll'yi (sürüm 1.0.0.0) kaydettirdiğiniz bir senaryo düşünün. Daha sonra myComp.dll sürüm 2.0.0.0'ı kaydettiriyorsunuz. Bilgisayardaki tüm COM istemci uygulamalarının myComp.dll sürüm 2.0.0.0 kullandığını öğreniyor ve myComponent.dll sürüm 1.0.0.0'ın kaydını kaldırmaya karar veriyorsunuz. Bu kayıt defteri düzeni myComp.dll sürüm 1.0.0.0'ın kaydını kaldırmanıza olanak verir, çünkü yalnızca sürüm 1.0.0.0 alt anahtarı kaldırılmıştır.

Regasm.exe kullanarak bir derleme kaydettikten sonra, herhangi bir COM istemcisinden etkinleştirilebilmek için [genel derleme önbelleğine](../app-domains/gac.md) yükleyebilirsiniz. Derleme yalnızca tek bir uygulamayla etkinleştirilecekse, onu söz konusu uygulamanın dizinine yerleştirebilirsiniz.

## <a name="examples"></a>Örnekler

Aşağıdaki komut, 'de `myTest.dll`yer alan tüm ortak sınıfları kaydeder.

```console
regasm myTest.dll
```

Aşağıdaki komut, gerekli `myTest.reg`tüm kayıt defteri girişlerini içeren dosyayı oluşturur. Bu komut, kayıt defterini güncelleştirmez.

```console
regasm myTest.dll /regfile:myTest.reg
```

Aşağıdaki komut, içerdiği `myTest.dll`tüm ortak sınıfları kaydeder ve 'de `myTest.tlb` `myTest.dll`tanımlanan tüm ortak türlerin tanımlarını içeren tür kitaplığını oluşturur ve kaydeder.

```console
regasm myTest.dll /tlb:myTest.tlb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Tlbexp.exe (Tip Kütüphane İhracatçısı)](tlbexp-exe-type-library-exporter.md)
- [Tlbimp.exe (Tip Kitaplığı İthalatçısı)](tlbimp-exe-type-library-importer.md)
- [Derlemeleri COM ile Kaydetme](../interop/registering-assemblies-with-com.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
