---
title: Regasm.exe (Derleme Kayıt Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Assembly Registration tool
- assemblies [.NET Framework], registering
- Regasm.exe
- registering assemblies
ms.assetid: e190e342-36ef-4651-a0b4-0e8c2c0281cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11ccdb4c75af2b37595d9be977f2ab881ebe1184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408752"
---
# <a name="regasmexe-assembly-registration-tool"></a>Regasm.exe (Derleme Kayıt Aracı)
Derleme Kayıt aracı, derleme içindeki meta verileri okur ve kayıt defterine gerekli girişleri ekler, bu da COM istemcilerinin şeffaf olarak .NET Framework sınıfları oluşturmalarına izin verir. Sınıf kaydettirildikten sonra, COM istemcileri artık sınıfı bir COM sınıfıymış gibi kullanabilir. Sınıf yalnızca bir defa, derleme yüklenirken kaydettirilir. Derleme içindeki sınıf örnekleri gerçekten kaydettirilene kadar COM'dan oluşturulamaz.  
  
 Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
regasm assemblyFile [options]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|*AssemblyFile*|COM ile kaydettirilecek derleme.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/ codebase**|Kayıt defterinde bir Kod Temeli girişi oluşturur. Kod Temeli girişi, genel derleme önbelleğinde yüklü olmayan bir derleme için dosya yolunu belirtir. Sonrasında genel derleme önbelleğine kaydettiriyor olduğunuz derlemeyi yükleyecekseniz bu seçeneği belirtmemelisiniz. *AssemblyFile* belirlediğiniz bağımsız değişkeni **/ codebase** seçeneği olmalıdır bir [tanımlayıcı adlı derleme](../../../docs/framework/app-domains/strong-named-assemblies.md).|  
|**/ kayıtlı**|Bu aracın yalnızca zaten kayıtlı durumdaki tür kitaplıklarına başvuracağını belirtir.|  
|**/asmpath:Directory**|Derleme başvuruları içeren bir dizini belirtir. İle birlikte kullanılmalıdır **/regfile** seçeneği.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/ regfile** [**:** *regFile*]|Gerekli kayıt defteri girdilerini içeren derleme için belirtilen .reg dosyasını oluşturur. Bu seçeneği belirtmek kayıt defterini değiştirmez. Bu seçenek ile kullanamazsınız **/u** veya **TLB** seçenekleri.|  
|**/ Sessiz** veya   **/s**|Başarı iletilerinin görüntülenmesini bastırır.|  
|**TLB** [**:** *typeLibFile*]|Belirtilen derlemeden, derleme içinde tanımlanmış erişilebilir türlerin tanımlarını içeren bir tür kitaplığı oluşturur.|  
|**/ kaydı** veya **/u**|Bulunan creatable sınıfları kaydını siler *assemblyFile*. Bu seçeneği kullanmamak, Regasm.exe'nin derlemedeki oluşturulabilir sınıfları kaydettirmesine neden olur.|  
|**/verbose**|Ayrıntılı modu belirtir; görüntüler herhangi bir listesini başvurulan derlemeler için tür kitaplığı, belirtilen zaman oluşturulması gereken **TLB** seçeneği.|  
|**/?** veya   **/Yardım**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
>  Regasm.exe komut satırı seçenekleri büyük/küçük harfe duyarsızdır. Seçeneğin, yalnızca onu benzersiz şekilde tanımlamaya yetecek kadarını sağlamanız yeterlidir. Örneğin, **/n** eşdeğerdir **/nologo** ve **/t:** *outfile.tlb* eşdeğerdir **TLB:**  *OutFile.tlb*.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz **/regfile** değişiklikleri doğrudan kayıt defterinde değişiklik yapmadan yerine kayıt defteri girdileri içeren bir .reg dosyasını oluşturmak için seçeneği. Kayıt Defteri Düzenleyicisi (Regedit.exe) aracı ile .reg dosyasını içe aktararak, bir bilgisayarda kayıt defterini güncelleştirebilirsiniz. .reg dosyasının, kullanıcı tarafından tanımlanan kayıt işlevleriyle yapılabilen kayıt defteri güncelleştirmelerini içermediğini unutmayın.  Unutmayın **/regfile** seçeneği yalnızca yönetilen sınıflar için kayıt defteri girdileri yayar.  Bu seçenek girişlerinde yayma değil `TypeLibID`s veya `InterfaceID`s.  
  
 Belirttiğinizde **TLB** seçeneği Regasm.exe oluşturur ve derlemesinde türlerini açıklayan bir tür kitaplığı kaydeder. RegAsm.exe oluşturulan tür kitaplıklarını geçerli çalışma dizinine veya çıktı dosyası için belirtilen dizine yerleştirir. Diğer derlemelere başvuran bir derleme için tür kitaplığı oluşturmak, bazı tür kitaplıklarının tek seferde oluşturulmasına neden olabilir. Tür kitaplığı gibi geliştirme araçları tür bilgiler sağlamak için kullanabileceğiniz [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]. Kullanılamaz **TLB** kaydetmekte olduğunuz derleme tür kitaplığı içeri Aktarıcı tarafından oluşturduysa seçeneği ([Tlbimp.exe](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)). Bir tür kitaplığından içeri aktarılmış bir derlemeden bir tür kitaplığını dışarı aktaramazsınız. Kullanarak **TLB** seçeneği tür kitaplığı dışarı Aktarıcı kullanarak aynı etkiye sahip ([Tlbexp.exe](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)) ve Tlbexp.exe bu üretir tür kitaplığının kaydı olmayan özel Regasm.exe.  Kullanırsanız **TLB** seçeneğine kayıtlı bir tür kitaplığı, kullanabileceğiniz **TLB** seçeneğini **/ kaydı** seçeneği için tür kitaplığı kaydı silindi. İki seçeneği birlikte kullandığınızda tür kitaplığının ve arabirim girdilerinin kaydını kaldırırsınız, bu da kayıt defterini önemli ölçüde temizleyebilir.  
  
 Bir derlemeyi COM tarafından kullanılması için kaydettirdiğinize, Regasm.exe girdileri yerel bilgisayardaki kayıt defterine ekler. Daha ayrıntılı şekilde söylemek gerekirse, aynı derlemenin birden fazla sürümünün bir bilgisayarda yan yana çalışmasına olanak veren sürüme bağlı kayıt defteri anahtarları oluşturur. Bir derleme ilk kez kaydettirildiğinde, derleme için bir üst düzey anahtar, o sürüm için de benzersiz bir alt anahtar oluşturulur. Derlemenin yeni bir sürümünü her kaydettirdiğinizde, Regasm.exe yeni sürüm için bir alt anahtar oluşturur.  
  
 Örneğin, COM tarafından kullanılmak üzere yönetilen bileşen myComp.dll'yi (sürüm 1.0.0.0) kaydettirdiğiniz bir senaryo düşünün. Daha sonra myComp.dll sürüm 2.0.0.0'ı kaydettiriyorsunuz. Bilgisayardaki tüm COM istemci uygulamalarının myComp.dll sürüm 2.0.0.0 kullandığını öğreniyor ve myComponent.dll sürüm 1.0.0.0'ın kaydını kaldırmaya karar veriyorsunuz. Bu kayıt defteri düzeni myComp.dll sürüm 1.0.0.0'ın kaydını kaldırmanıza olanak verir, çünkü yalnızca sürüm 1.0.0.0 alt anahtarı kaldırılmıştır.  
  
 RegAsm.exe kullanarak bir derlemeye kaydolduktan sonra bunu yükleyebilirsiniz [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md) böylece herhangi bir COM istemciden etkinleştirilebilir. Derleme yalnızca tek bir uygulamayla etkinleştirilecekse, onu söz konusu uygulamanın dizinine yerleştirebilirsiniz.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut içinde yer alan tüm ortak sınıfların kaydeder `myTest.dll`.  
  
```  
regasm myTest.dll  
```  
  
 Aşağıdaki komut dosyasını oluşturur `myTest.reg`, tüm gerekli kayıt defteri girişleri içerir. Bu komut, kayıt defterini güncelleştirmez.  
  
```  
regasm myTest.dll /regfile:myTest.reg  
```  
  
 Aşağıdaki komut içinde yer alan tüm ortak sınıfların kaydeder `myTest.dll`, oluşturur ve tür kitaplığı kaydeder `myTest.tlb`, tanımlanan tüm ortak türlerinin tanımlarını içeren `myTest.dll`.  
  
```  
regasm myTest.dll /tlb:myTest.tlb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [Bütünleştirilmiş Kodları COM ile Kaydetme](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
