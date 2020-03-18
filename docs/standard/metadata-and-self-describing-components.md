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
ms.openlocfilehash: a4f4c0e1af379d31c5b478472780d5c7de813bf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121940"
---
# <a name="metadata-and-self-describing-components"></a>Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler

Geçmişte, bir dilde yazılmış bir yazılım bileşeni (.exe veya .dll) başka bir dilde yazılmış bir yazılım bileşenini kolayca kullanamaz. COM bu sorunu çözme yolunda bir adım sağladı. .NET Framework, derleyicilerin tüm modüllere ve derlemelere ek bildirim bilgileri yarayabilmelerine izin vererek bileşen etkileşimini daha da kolaylaştırır. Meta veri adı verilen bu bilgiler, bileşenlerin sorunsuz bir şekilde etkileşimkurmasına yardımcı olur.

 Meta veriler, programınızı açıklayan ve ortak bir dilde taşınabilir yürütülebilir (PE) dosyada veya bellekte depolanan ikili bilgilerdir. Kodunuzu bir PE dosyasına derlediğinizde, meta veriler dosyanın bir bölümüne eklenir ve kodunuz Microsoft ara diline (MSIL) dönüştürülür ve dosyanın başka bir bölümüne eklenir. Bir modül veya derlemede tanımlanan ve başvurulan her tür ve üye meta veriler içinde tanımlanır. Kod yürütüldüğünde, çalışma zamanı meta verileri belleğe yükler ve kodunuzun sınıfları, üyeleri, kalıtım ve benzeri bilgileri bulmak için bu verilere başvurur.

 Meta veriler, kodunuzda tanımlanan her tür ve üyeyi dilden bağımsız bir şekilde tanımlar. Meta veriler aşağıdaki bilgileri depolar:

- Derlemenin açıklaması.

  - Kimlik (ad, sürüm, kültür, ortak anahtar).

  - Dışa aktarılan türler.

  - Bu derlemenin bağlı olduğu diğer derlemeler.

  - Çalıştırmak için güvenlik izinleri gerekiyordu.

- Türlerin açıklaması.

  - Ad, görünürlük, taban sınıf ve uygulanan arabirimler.

  - Üyeler (yöntemler, alanlar, özellikler, olaylar, iç içe türleri).

- Öznitelik.

  - Türleri ve üyeleri değiştiren ek açıklayıcı öğeler.

## <a name="benefits-of-metadata"></a>Meta verilerin Faydaları

Meta veriler daha basit bir programlama modelinin anahtarıdır ve Arabirim Tanımı Dili (IDL) dosyaları, üstbilgi dosyaları veya bileşen başvurusu için herhangi bir dış yöntem gereksinimini ortadan kaldırır. Meta veriler .NET Framework dillerinin kendilerini hem geliştirici hem de kullanıcı tarafından görülmeyen, dilden bağımsız bir şekilde otomatik olarak tanımlamasını sağlar. Ayrıca, meta veriler özniteliklerin kullanımı yoluyla genişletilebilir. Meta veriler aşağıdaki önemli yararları sağlar:

- Kendi kendini açıklayan dosyalar.

  Ortak dil çalışma zamanı modülleri ve derlemeleri kendi kendini tanımlar. Bir modülün meta verileri, başka bir modülle etkileşim kurmak için gereken her şeyi içerir. Meta veriler COM'da IDL işlevselliğini otomatik olarak sağlar, böylece hem tanım hem de uygulama için bir dosya kullanabilirsiniz. Çalışma zamanı modülleri ve montajları bile işletim sistemi ile kayıt gerektirmez. Sonuç olarak, çalışma zamanı tarafından kullanılan açıklamalar her zaman derlenmiş dosyanızdaki gerçek kodu yansıtır ve bu da uygulama güvenilirliğini artırır.

- Dil birlikte çalışabilirliği ve daha kolay bileşen tabanlı tasarım.

  Meta veriler, farklı bir dilde yazılmış bir PE dosyasından bir sınıfı devralmanız için derlenmiş kod hakkında gereken tüm bilgileri sağlar. Herhangi bir yönetilen dilde yazılmış herhangi bir sınıfın örneğini (ortak dil çalışma süresini hedefleyen herhangi bir dil) açık bir şekilde işleme konusunda endişelenmeden veya özel birlikte çalışabilirlik kodu kullanmadan oluşturabilirsiniz.

- Öznitelik.

  .NET Framework, derlenen dosyanızda öznitelikler olarak adlandırılan belirli türde meta veri beyan etmenizi sağlar. Öznitelikler .NET Framework boyunca bulunabilir ve programınızın çalışma zamanında nasıl davranışta bulunduğunu daha ayrıntılı olarak denetlemek için kullanılır. Ayrıca, kullanıcı tanımlı özel öznitelikler aracılığıyla kendi özel meta verilerinizi .NET Framework dosyalarına yatabilirsiniz. Daha fazla bilgi için [Özniteliklere](../../docs/standard/attributes/index.md)bakın.

## <a name="metadata-and-the-pe-file-structure"></a>Meta Veri ve PE Dosya Yapısı

Metaveriler .NET Framework taşınabilir yürütülebilir (PE) dosyasının bir bölümünde saklanırken, Microsoft ara dili (MSIL) PE dosyasının başka bir bölümünde saklanır. Dosyanın metaveri bölümü bir dizi tablo ve yığın veri yapısı içerir. MSIL bölümü, MSIL kodu ve PE dosyasının metaveri bölümüne atıfta bulunan metaveri belirteçleri içerir. Örneğin, kodunuzu MSIL görüntülemek için [MSIL Desassembler (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) gibi araçları kullandığınızda meta veri belirteçleri ile karşılaşabilirsiniz.

### <a name="metadata-tables-and-heaps"></a>Metaveri Tabloları ve Yığınlar

Her metaveri tablosu, programınızın öğeleri hakkında bilgi içerir. Örneğin, bir metaveri tablosu kodunuzdaki sınıfları, başka bir tablo alanları, vb. açıklar. Eğer kodunuzda on sınıf varsa, sınıf tablosu her sınıf için bir tane olmak üzere on satır içerir. Metaveri tabloları diğer tablolara ve yığınlara atıfta bulunur. Örneğin, sınıfların metaveri tablosu, metotların tablosuna atıfta bulunur.

Metaveri, ayrıca, dört yığın yapısında bilgi tutar: Dize, blob, kullanıcı dizesi ve GUID. Türleri ve üyeleri adlandırmak için kullanılan tüm dizeler dize yığınında tutulur. Örneğin, bir yöntem tablosu belirli bir yöntemin adını doğrudan saklamaz; bunun yerine, dize yığınındaki yöntem adına işaret eder.

### <a name="metadata-tokens"></a>Meta Veri Belirteçleri

Her metaveri tablosunun her satırı, PE dosyasının MSIL bölümünde bir metaveri belirteci tarafından benzersiz olarak tanımlanır. Metaveri belirteçleri, kavramsal olarak MSIL'de kalıcı olarak bulunan ve belirli bir metaveri tablosuna atıfta bulunan işaretçilere benzer.

Metaveri belirteci, dört baytlık bir sayıdır. Üstteki bayt, belirtecin atıfta bulunduğu belirli bir metaveri tablosunu (yöntem, tür vb.) belirtir. Diğer üç bayt, metaveri tablosunda açıklanan programlama öğesine karşılık gelen satırı belirtir. Eğer C# dilinde bir yöntem tanımlayıp bunu bir PE dosyası olarak derlerseniz, PE dosyasının MSIL bölümünde aşağıdaki metaveri belirteci bulunabilir:

`0x06000004`

Üst bayt`0x06`( ) bunun bir **MethodDef** belirteci olduğunu gösterir. Alt üç bayt`000004`( ) bu yöntem tanımıaçıklayan bilgiler için **MethodDef** tablosunun dördüncü satırında bakmak için ortak dil çalışma zamanı söyler.

### <a name="metadata-within-a-pe-file"></a>Bir PE Dosyasının İçindeki Metaveriler

Bir program ortak dil çalışma zamanı için derlendiğinde, üç bölümden oluşan bir PE dosyasına dönüştürülür. Aşağıdaki tabloda her bölümün içeriği açıklanmaktadır.

|PE bölümü|PE bölümünün içerikleri|
|----------------|----------------------------|
|PE üst bilgisi|PE dosyasının ana bölümlerinin ve giriş noktası adresinin dizini.<br /><br /> Çalışma zamanı, bu bilgileri, dosyayı bir PE dosyası olarak tanımlamak ve programı belleğe yüklerken yürütmenin nereden başlayacağını belirlemek için kullanır.|
|MSIL yönergeleri|Kodunuzu oluşturan Microsoft ara dili (MSIL) yönergeleri. Birçok MSIL yönergesi metaveri belirteçleri ile birlikte bulunur.|
|Meta Veriler|Metaveri tabloları ve yığınlar Çalışma zamanı, bu bölümü, kodunuzdaki tüm türler ve üyeler hakkında bilgi kaydetmek için kullanır. Bu bölüm ayrıca özel öznitelikler ve güvenlik bilgileri de içerir.|

## <a name="run-time-use-of-metadata"></a>Meta Verilerin Çalışma Zamanında Kullanımı

Meta verileri ve ortak dil çalışma süresindeki rolünü daha iyi anlamak için, basit bir program oluşturmak ve meta verilerin çalışma süresini nasıl etkilediğini göstermek yararlı olabilir. Aşağıdaki kod örneği, bir sınıf `MyApp`içinde iki yöntem gösterir. Yöntem `Main` sadece iki toplam bağımsız `Add` değişkenin toplamını döndürürken, yöntem program giriş noktasıdır.

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

Kod çalıştığında, çalışma zamanı modülü belleğe yükler ve bu sınıfın meta verilerine başvurur. Yüklendikten sonra, çalışma zamanı yöntemin Microsoft ara dili (MSIL) akışının hızlı yerel makine yönergelerine dönüştürmek için kapsamlı bir çözümleme gerçekleştirir. Çalışma süresi, MSIL yönergelerini gerektiğinde bir defada yerel makine koduna dönüştürmek için tam zamanında (JIT) derleyici kullanır.

Aşağıdaki örnek, önceki kodun `Main` işlevinden üretilen MSIL bölümünü gösterir. [MSIL Desassembler (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md)kullanarak herhangi bir .NET Framework uygulamasından MSIL ve meta verileri görüntüleyebilirsiniz.

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

JIT derleyicisi tüm yöntem için MSIL okur, iyice analiz eder ve yöntem için verimli yerel talimatlar oluşturur. At `IL_000d`, `Add` yöntem için bir meta`/*` `06000003 */`veri belirteci ( ) karşılaşılan ve çalışma zamanı **MethodDef** tablosunun üçüncü satırına danışmak için belirteci kullanır.

Aşağıdaki tablo, **metodu** açıklayan meta veri belirteci tarafından `Add` başvurulan MethodDef tablosunun bir bölümünü gösterir. Diğer meta veri tabloları bu derlemede var ve kendi benzersiz değerleri olsa da, yalnızca bu tablo tartışılır.

|Satır|Göreli Sanal Adres (RVA)|ImplFlags|Bayraklar|Adı<br /><br /> (String yığınına işaret eder.)|İmza (Blob yığınına işaret eder.)|
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|
|1|0x00002050|IL<br /><br /> Yönetilen|Genel<br /><br /> ReuseSlot<br /><br /> Specialname<br /><br /> RTSpecialName<br /><br /> Ctor|.ctor (yapıcı)||
|2|0x00002058|IL<br /><br /> Yönetilen|Genel<br /><br /> Statik<br /><br /> ReuseSlot|Ana|Dize|
|3|0x0000208c|IL<br /><br /> Yönetilen|Genel<br /><br /> Statik<br /><br /> ReuseSlot|Ekle|int, int, int|

Tablonun her sütunu kodunuz hakkında önemli bilgiler içerir. **RVA** sütunu, çalışma zamanının bu yöntemi tanımlayan MSIL'in başlangıç bellek adresini hesaplamasına olanak tanır. **ImplFlags** ve **Flags** sütunları yöntemi açıklayan bit maskeleri içerir (örneğin, yöntemin ortak mı yoksa özel mi olduğu). **Ad** sütunu dize yığınından yöntemin adını diziye diziler. **İmza** sütunu, yöntemin imzasının blob yığınındaki tanımını dizine dizine dizine dizir.

Çalışma süresi, üçüncü satırdaki **RVA** sütunundan istenen mahsup adresini hesaplar ve bu adresi JIT derleyicisine döndürür ve bu adres yeni adrese gider. JIT derleyicisi, başka bir meta veri belirteciyle karşılaşAna ve işlem yinelenene kadar MSIL'i yeni adreste işlemeye devam eder.

Meta verileri kullanarak, çalışma zamanı, kodunuzu yüklemek ve yerel makine yönergelerine işlemek için gereken tüm bilgilere erişebilir. Bu şekilde, meta veriler kendi kendini açıklayan dosyaları ve ortak tür sistemiyle birlikte diller arası devralmayı sağlar.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Öznitelikler](../../docs/standard/attributes/index.md)|Öznitelikleri nasıl uygulayacağımı, özel öznitelikleri nasıl yazacağıve özniteliklerde depolanan bilgileri nasıl alınacağı açıklanır.|
