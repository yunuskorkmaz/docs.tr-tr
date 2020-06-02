---
title: Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- runtime, metadata
- languages, interoperability
- portable executable files, metadata
- self-describing files
- metadata, about metadata
- common language runtime, metadata
- PE files, metadata
- components [.NET Framework], metadata
ms.assetid: 3dd13c5d-a508-455b-8dce-0a852882a5a7
ms.openlocfilehash: 5327bd70b05bac8970fa9802fb15e94ba5f686c8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290064"
---
# <a name="metadata-and-self-describing-components"></a>Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler

Geçmişte, bir dilde yazılmış bir yazılım bileşeni (. exe veya. dll), başka bir dilde yazılmış bir yazılım bileşenini kolayca kullanamaz. COM, bu sorunu çözmeye yönelik bir adım sağladı. .NET Framework, derleyicilerin tüm modüller ve derlemelere ek bildirime dayalı bilgiler yaymasına izin vererek bileşeni birlikte çalışabilirliği daha da kolaylaştırır. Meta veri olarak adlandırılan bu bilgiler, bileşenlerin sorunsuz bir şekilde etkileşim kurmasına yardımcı olur.

 Meta veriler, programınızı ortak bir dil çalışma zamanı Taşınabilir çalıştırılabilir (PE) dosyasında ya da bellekte depolanan bir ikili bilgi olarak tanımlar. Kodunuzu bir PE dosyasına derlerken meta veriler dosyanın bir kısmına eklenir ve kodunuz Microsoft ara dili 'ne (MSIL) dönüştürülüp dosyanın başka bir bölümüne eklenir. Bir modülde veya derlemede tanımlanan ve başvurulan her tür ve üye meta veriler içinde açıklanmıştır. Kod yürütüldüğünde, çalışma zamanı meta verileri belleğe yükler ve kodunuzun sınıfları, üyeleri, devralma vb. hakkında bilgi edinmek için ona başvurur.

 Meta veriler, kodunuzda tanımlanan her tür ve üyeyi dilden bağımsız bir şekilde tanımlar. Meta veriler aşağıdaki bilgileri depolar:

- Derlemenin açıklaması.

  - Kimlik (ad, sürüm, kültür, ortak anahtar).

  - İçe aktarılmış türler.

  - Bu derlemenin bağımlı olduğu diğer derlemeler.

  - Çalıştırmak için gereken güvenlik izinleri.

- Türlerin açıklaması.

  - Ad, görünürlük, temel sınıf ve arabirimler uygulandı.

  - Üyeler (Yöntemler, alanlar, özellikler, olaylar, iç içe türler).

- Özelliklerine.

  - Türleri ve üyeleri değiştiren ek tanımlayıcı öğeler.

## <a name="benefits-of-metadata"></a>Meta verilerin avantajları

Meta veriler, daha basit bir programlama modelinin anahtarıdır ve arabirim tanım dili (IDL) dosyaları, üst bilgi dosyaları veya bileşen başvurusunun herhangi bir dış yöntemi için gereksinimi ortadan kaldırır. Meta veriler, hem geliştirici hem de Kullanıcı tarafından görülmeyen .NET Framework dillerin kendisini otomatik olarak dilden bağımsız bir şekilde tanımlamasını sağlar. Ayrıca, meta veriler özniteliklerin kullanımı ile genişletilebilir. Meta veriler aşağıdaki başlıca avantajları sağlar:

- Kendi kendine açıklama dosyaları.

  Ortak dil çalışma zamanı modülleri ve derlemeleri kendi kendini tanımlar. Modülün meta verileri, başka bir modülle etkileşimde bulunmak için gereken her şeyi içerir. Meta veriler, COM 'daki IDL işlevlerini otomatik olarak sağlar, böylece hem tanım hem de uygulama için bir dosya kullanabilirsiniz. Çalışma zamanı modülleri ve derlemeler, işletim sistemiyle kayıt gerektirmez. Sonuç olarak, çalışma zamanı tarafından kullanılan açıklamalar her zaman derlenmiş dosyanızdaki gerçek kodu yansıtır ve bu da uygulama güvenilirliğini artırır.

- Dil birlikte çalışabilirliği ve daha kolay bileşen tabanlı tasarım.

  Meta veriler, farklı bir dilde yazılmış bir PE dosyasından bir sınıfı devralması için derlenmiş kod hakkında gereken tüm bilgileri sağlar. Açık sıralama veya özel birlikte çalışabilirlik kodu kullanma hakkında endişelenmeden, herhangi bir yönetilen dilde (ortak dil çalışma zamanını hedefleyen herhangi bir dilde) yazılmış herhangi bir sınıfın örneğini oluşturabilirsiniz.

- Özelliklerine.

  .NET Framework, derlenmiş dosyanızda öznitelikler olarak adlandırılan belirli meta veri türlerini bildirmenize olanak tanır. Öznitelikler, .NET Framework tamamında bulunabilir ve programınızın çalışma zamanında nasıl davranacağını daha ayrıntılı olarak denetlemek için kullanılır. Ayrıca, Kullanıcı tanımlı özel öznitelikler aracılığıyla .NET Framework dosyalara kendi özel meta verilerinizi de yayabilirsiniz. Daha fazla bilgi için bkz. [öznitelikler](attributes/index.md).

## <a name="metadata-and-the-pe-file-structure"></a>Meta Veri ve PE Dosya Yapısı

Metaveriler .NET Framework taşınabilir yürütülebilir (PE) dosyasının bir bölümünde saklanırken, Microsoft ara dili (MSIL) PE dosyasının başka bir bölümünde saklanır. Dosyanın metaveri bölümü bir dizi tablo ve yığın veri yapısı içerir. MSIL bölümü, MSIL kodu ve PE dosyasının metaveri bölümüne atıfta bulunan metaveri belirteçleri içerir. Örneğin, kodunuzun MSIL 'sini görüntülemek için [MSIL Disassembler (ıldadsm. exe)](../framework/tools/ildasm-exe-il-disassembler.md) gibi araçları kullandığınızda meta veri belirteçleriyle karşılaşabilirsiniz.

### <a name="metadata-tables-and-heaps"></a>Metaveri Tabloları ve Yığınlar

Her metaveri tablosu, programınızın öğeleri hakkında bilgi içerir. Örneğin, bir metaveri tablosu kodunuzdaki sınıfları, başka bir tablo alanları, vb. açıklar. Eğer kodunuzda on sınıf varsa, sınıf tablosu her sınıf için bir tane olmak üzere on satır içerir. Metaveri tabloları diğer tablolara ve yığınlara atıfta bulunur. Örneğin, sınıfların metaveri tablosu, metotların tablosuna atıfta bulunur.

Metaveri, ayrıca, dört yığın yapısında bilgi tutar: Dize, blob, kullanıcı dizesi ve GUID. Türleri ve üyeleri adlandırmak için kullanılan tüm dizeler dize yığınında tutulur. Örneğin, bir yöntem tablosu belirli bir yöntemin adını doğrudan saklamaz; bunun yerine, dize yığınındaki yöntem adına işaret eder.

### <a name="metadata-tokens"></a>Meta Veri Belirteçleri

Her metaveri tablosunun her satırı, PE dosyasının MSIL bölümünde bir metaveri belirteci tarafından benzersiz olarak tanımlanır. Metaveri belirteçleri, kavramsal olarak MSIL'de kalıcı olarak bulunan ve belirli bir metaveri tablosuna atıfta bulunan işaretçilere benzer.

Metaveri belirteci, dört baytlık bir sayıdır. Üstteki bayt, belirtecin atıfta bulunduğu belirli bir metaveri tablosunu (yöntem, tür vb.) belirtir. Diğer üç bayt, metaveri tablosunda açıklanan programlama öğesine karşılık gelen satırı belirtir. Eğer C# dilinde bir yöntem tanımlayıp bunu bir PE dosyası olarak derlerseniz, PE dosyasının MSIL bölümünde aşağıdaki metaveri belirteci bulunabilir:

`0x06000004`

Üstteki bayt ( `0x06` ), bu bir **MethodDef** belirteci olduğunu gösterir. Daha az üç bayt ( `000004` ), ortak dil çalışma zamanına, bu yöntem tanımını açıklayan bilgiler Için **MethodDef** tablosunun dördüncü satırına bakmasını söyler.

### <a name="metadata-within-a-pe-file"></a>Bir PE Dosyasının İçindeki Metaveriler

Bir program ortak dil çalışma zamanı için derlendiğinde, üç bölümden oluşan bir PE dosyasına dönüştürülür. Aşağıdaki tabloda her bölümün içeriği açıklanmaktadır.

|PE bölümü|PE bölümünün içerikleri|
|----------------|----------------------------|
|PE üst bilgisi|PE dosyasının ana bölümlerinin ve giriş noktası adresinin dizini.<br /><br /> Çalışma zamanı, bu bilgileri, dosyayı bir PE dosyası olarak tanımlamak ve programı belleğe yüklerken yürütmenin nereden başlayacağını belirlemek için kullanır.|
|MSIL yönergeleri|Kodunuzu oluşturan Microsoft ara dili (MSIL) yönergeleri. Birçok MSIL yönergesi metaveri belirteçleri ile birlikte bulunur.|
|Meta Veriler|Metaveri tabloları ve yığınlar Çalışma zamanı, bu bölümü, kodunuzdaki tüm türler ve üyeler hakkında bilgi kaydetmek için kullanır. Bu bölüm ayrıca özel öznitelikler ve güvenlik bilgileri de içerir.|

## <a name="run-time-use-of-metadata"></a>Meta Verilerin Çalışma Zamanında Kullanımı

Ortak dil çalışma zamanında meta verileri ve rolünü daha iyi anlamak için, basit bir program oluşturmak ve meta verilerin çalışma zamanı ömrünü nasıl etkilediğini göstermek yararlı olabilir. Aşağıdaki kod örneği, adlı bir sınıf içinde iki yöntemi gösterir `MyApp` . Yöntemi `Main` program giriş noktasıdır, ancak `Add` Yöntem yalnızca iki tamsayı bağımsız değişkenin toplamını döndürür.

```vb
Public Class MyApp
   Public Shared Sub Main()
      Dim ValueOne As Integer = 10
      Dim ValueTwo As Integer = 20
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo))
   End Sub

   Public Shared Function Add(One As Integer, Two As Integer) As Integer
      Return (One + Two)
   End Function
End Class
```

```csharp
using System;
public class MyApp
{
   public static int Main()
   {
      int ValueOne = 10;
      int ValueTwo = 20;
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo));
      return 0;
   }
   public static int Add(int One, int Two)
   {
      return (One + Two);
   }
}
```

Kod çalıştığında, çalışma zamanı modülü belleğe yükler ve bu sınıfa ait meta verileri çalıştırır. Yüklendikten sonra, çalışma zamanı, yöntemin Microsoft ara dili (MSIL) akışının kapsamlı analizini gerçekleştirerek hızlı yerel makine yönergelerine dönüştürür. Çalışma zamanı tam zamanında (JıT) derleyicisini kullanarak MSIL talimatlarını aynı anda bir yönteme yerel makine koduna dönüştürür.

Aşağıdaki örnek, önceki kodun işlevinden üretilen MSIL 'in bir parçasını gösterir `Main` . MSIL [Disassembler (ıldadsm. exe)](../framework/tools/ildasm-exe-il-disassembler.md)kullanarak herhangi bir .NET Framework uygulamadan MSIL ve meta verileri görüntüleyebilirsiniz.

```console
.entrypoint
.maxstack  3
.locals ([0] int32 ValueOne,
         [1] int32 ValueTwo,
         [2] int32 V_2,
         [3] int32 V_3)
IL_0000:  ldc.i4.s   10
IL_0002:  stloc.0
IL_0003:  ldc.i4.s   20
IL_0005:  stloc.1
IL_0006:  ldstr      "The Value is: {0}"
IL_000b:  ldloc.0
IL_000c:  ldloc.1
IL_000d:  call int32 ConsoleApplication.MyApp::Add(int32,int32) /* 06000003 */
```

JıT derleyicisi, tüm yöntemi için MSIL 'yi okur, onu tamamen analiz eder ve yöntemi için etkili yerel yönergeler oluşturur. `IL_000d`' De, yöntemi () için bir meta veri belirtecine `Add` `/*` `06000003 */` rastlandı ve çalışma zamanı, **MethodDef** tablosunun üçüncü satırına danışması için belirteci kullanır.

Aşağıdaki tabloda, yöntemini açıklayan meta veri belirtecinin başvurduğu **MethodDef** tablosunun bir kısmı gösterilmektedir `Add` . Bu derlemede diğer meta veri tabloları var ve kendi benzersiz değerleri var olsa da, yalnızca bu tablo ele alınmıştır.

|Satır|Göreli sanal adres (RVA)|ImplFlags|Bayraklar|Name<br /><br /> (Dize yığınına işaret eder.)|İmza (blob yığınına Işaret eder.)|
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|
|1|0x00002050|IL<br /><br /> Yönetilen|Ortak<br /><br /> Reusespartisi<br /><br /> SpecialName<br /><br /> RTSpecialName<br /><br /> . ctor|. ctor (Oluşturucu)||
|2|0x00002058|IL<br /><br /> Yönetilen|Ortak<br /><br /> Statik<br /><br /> Reusespartisi|Ana|Dize|
|3|0x0000208c|IL<br /><br /> Yönetilen|Ortak<br /><br /> Statik<br /><br /> Reusespartisi|Ekle|int, int, int|

Tablonun her sütunu, kodunuz hakkında önemli bilgiler içerir. **RVA** sütunu, çalışma zamanının bu YÖNTEMI tanımlayan MSIL 'nin başlangıç belleği adresini hesaplamasını sağlar. **ImplFlags** ve **Flags** sütunları, yöntemi tanımlayan bitmaskeleri içerir (örneğin, yöntemin genel mi yoksa özel mi olduğunu belirtir). **Ad** sütunu, dize yığınından yöntemin adını dizine ekler. **İmza** sütunu, blob yığınındaki yöntem imzasının tanımını dizinler.

Çalışma zamanı, üçüncü satırdaki **RVA** sütunundan istenen konum adresini hesaplar ve bu adresi, daha sonra yeni adrese devam eden JIT derleyicisine döndürür. JıT derleyicisi, başka bir meta veri belirteciyle karşılaşana kadar yeni adreste MSIL işlemeye devam eder ve işlem yinelenir.

Meta verileri kullanarak, çalışma zamanının kodunuzu yüklemesi ve yerel makine yönergelerine işlemesi için gereken tüm bilgilere erişimi vardır. Bu şekilde meta veriler, ortak tür sistemi, çapraz dil devralma ile birlikte kendi kendine açıklanabilen dosyaları ve bir arada sunar.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Öznitelikler](attributes/index.md)|Özniteliklerin nasıl uygulanacağını, özel özniteliklerin nasıl yazılacağını ve özniteliklerde depolanan bilgilerin nasıl alınacağını açıklar.|
