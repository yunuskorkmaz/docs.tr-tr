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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bc603d90ae4636ac50ab9cbabf7d176309498b4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909266"
---
# <a name="metadata-and-self-describing-components"></a>Meta Veriler ve Kendiliğinden Açıklayıcı Bileşenler

Geçmişte, tek bir dilde yazılmış bir yazılım bileşeni (.exe veya .dll) kolayca başka bir dilde yazılmış bir yazılım bileşeni kullanılamadı. Bu sorunun çözümüne bilgilerinizin COM sağlanır. .NET Framework bileşeni birlikte çalışabilirlik bile tüm modül ve derlemelerdeki ek bildirim temelli bilgileri yaymak derleyiciler vererek kolaylaştırır. Meta verileri, adlı bu bilgi, sorunsuz bir şekilde etkileşime geçmek için bileşenler yardımcı olur.

 Meta verileri tanımlayan bir ortak dil çalışma zamanı taşınabilir yürütülebilir (PE) dosyası veya bellekte depolanır, programınızın ikili bilgilerdir. Bir PE dosyası olarak kodunuzu derlediğinizde, meta veri dosyasının bir bölümünü eklenir ve kodunuzu Microsoft Ara dili (MSIL) dönüştürülür ve başka bir dosyanın bölümünü eklenir. Tüm türler ve üyeler tanımlanan ve bir modül veya derleme meta verileri içinde açıklanmıştır. Kod yürütüldüğünde, çalışma zamanı meta verileri belleğe ve kodunuzun sınıfları, üyeleri, devralma ve benzeri hakkında bilgi bulmak için başvuruyor.

 Her tür ve üye kodunuzda bir dilden biçimde tanımlı meta veriler açıklanmaktadır. Meta verileri aşağıdaki bilgileri depolar:

- Derleme tanımı.

  - Kimliği (adı, sürüm, kültür, ortak anahtar).

  - Dışarı aktarılan türler.

  - Bu derlemeye bağımlı diğer derlemeler.

  - Çalıştırmak için gereken güvenlik izinleri.

- Tür tanımı.

  - Ad, görünürlük, temel sınıfı ve uygulanan arabirimleri.

  - Üyeler (yöntemler, alanlar, özellikleri, olaylar, iç içe geçmiş türler).

- Öznitelikleri.

  - Türler ve üyeler değiştirme ek tanımlayıcı öğeler.

## <a name="benefits-of-metadata"></a>Meta veri avantajları

Meta verileri anahtar daha basit bir programlama modeli ve arabirim tanımlama dili (IDL) dosyaları, üstbilgi dosyaları veya herhangi bir dış yöntemi bileşen başvuru ihtiyacını ortadan kaldırır. Meta veriler hem geliştiriciler hem de kullanıcı tarafından görünmeyen bir dilden biçimde kendilerini otomatik olarak tanımlamak .NET Framework dillerinde sağlar. Buna ek olarak, meta veri öznitelikleri kullanarak genişletilebilir. Meta veriler, aşağıdaki yararları sağlar:

- Kendiliğinden açıklayıcı dosyalar.

  Ortak dil çalışma zamanı modül ve derlemelerdeki kendiliğinden açıklayıcı. Bir modülün meta verileri başka bir modül ile etkileşim kurmak için gereken her şeyi içerir. Bir dosya için tanım ve uygulamayı kullanabilmeniz için meta verileri otomatik olarak IDL COM ile işlevlerini sağlar. Çalışma zamanı modül ve derlemelerdeki bile işletim sistemiyle kayıt gerektirmez. Sonuç olarak, her zaman çalışma zamanı tarafından kullanılan açıklamaları uygulama güvenilirliği artırır, derlenmiş dosyanızı gerçek kod yansıtır.

- Diller arası çalışabilirlik ve daha kolay bileşen tabanlı tasarım.

  Meta veriler hakkında derlenmiş kod, farklı bir dilde yazılmış bir PE dosyası devralınan bir sınıf gerekli tüm bilgileri sağlar. Tüm yönetilen (ortak dil çalışma zamanını hedefleyen bir dil) açık sıralama veya özel bir birlikte çalışabilirlik kodla hakkında endişelenmeden dilde herhangi bir sınıfın bir örneğini oluşturabilirsiniz.

- Öznitelikleri.

  .NET Framework meta verileri derlenmiş, dosyanıza öznitelikleri adlı, belirli türde bildirmek olanak sağlar. Öznitelikler, .NET Framework'de bulunabilir ve programınızın çalışma zamanında nasıl davranacağını daha ayrıntılı olarak denetlemek için kullanılır. Ayrıca, kullanıcı tanımlı özel öznitelikler aracılığıyla .NET Framework dosyalarına kendi özel meta veri gönderebilir. Daha fazla bilgi için [öznitelikleri](../../docs/standard/attributes/index.md).

## <a name="metadata-and-the-pe-file-structure"></a>Meta Veri ve PE Dosya Yapısı

Metaveriler .NET Framework taşınabilir yürütülebilir (PE) dosyasının bir bölümünde saklanırken, Microsoft ara dili (MSIL) PE dosyasının başka bir bölümünde saklanır. Dosyanın metaveri bölümü bir dizi tablo ve yığın veri yapısı içerir. MSIL bölümü, MSIL kodu ve PE dosyasının metaveri bölümüne atıfta bulunan metaveri belirteçleri içerir. Araçları gibi kullandığınızda metaveri belirteçleriyle karşılaşabilirsiniz [MSIL Disassembler (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md) kodunu görüntülemek için kodunuzun MSIL örneğin.

### <a name="metadata-tables-and-heaps"></a>Metaveri Tabloları ve Yığınlar

Her metaveri tablosu, programınızın öğeleri hakkında bilgi içerir. Örneğin, bir metaveri tablosu kodunuzdaki sınıfları, başka bir tablo alanları, vb. açıklar. Eğer kodunuzda on sınıf varsa, sınıf tablosu her sınıf için bir tane olmak üzere on satır içerir. Metaveri tabloları diğer tablolara ve yığınlara atıfta bulunur. Örneğin, sınıfların metaveri tablosu, metotların tablosuna atıfta bulunur.

Metaveri, ayrıca, dört yığın yapısında bilgi tutar: Dize, blob, kullanıcı dizesi ve GUID. Türleri ve üyeleri adlandırmak için kullanılan tüm dizeler dize yığınında tutulur. Örneğin, bir yöntem tablosu belirli bir yöntemin adını doğrudan saklamaz; bunun yerine, dize yığınındaki yöntem adına işaret eder.

### <a name="metadata-tokens"></a>Meta Veri Belirteçleri

Her metaveri tablosunun her satırı, PE dosyasının MSIL bölümünde bir metaveri belirteci tarafından benzersiz olarak tanımlanır. Metaveri belirteçleri, kavramsal olarak MSIL'de kalıcı olarak bulunan ve belirli bir metaveri tablosuna atıfta bulunan işaretçilere benzer.

Metaveri belirteci, dört baytlık bir sayıdır. Üstteki bayt, belirtecin atıfta bulunduğu belirli bir metaveri tablosunu (yöntem, tür vb.) belirtir. Diğer üç bayt, metaveri tablosunda açıklanan programlama öğesine karşılık gelen satırı belirtir. Eğer C# dilinde bir yöntem tanımlayıp bunu bir PE dosyası olarak derlerseniz, PE dosyasının MSIL bölümünde aşağıdaki metaveri belirteci bulunabilir:

```
0x06000004
```

Üstteki bayt (`0x06`) bu olduğunu belirten bir **MethodDef** belirteci. Alttaki üç bayt (`000004`) ortak dil çalışma dördüncü satırına bakmasını söyler **MethodDef** tablosu için bu yöntem tanımını açıklayan bilgiler.

### <a name="metadata-within-a-pe-file"></a>Bir PE Dosyasının İçindeki Metaveriler

Bir program ortak dil çalışma zamanı için derlendiğinde, üç bölümden oluşan bir PE dosyasına dönüştürülür. Aşağıdaki tabloda her bölümün içeriği açıklanmaktadır.

|PE bölümü|PE bölümünün içerikleri|
|----------------|----------------------------|
|PE üst bilgisi|PE dosyasının ana bölümlerinin ve giriş noktası adresinin dizini.<br /><br /> Çalışma zamanı, bu bilgileri, dosyayı bir PE dosyası olarak tanımlamak ve programı belleğe yüklerken yürütmenin nereden başlayacağını belirlemek için kullanır.|
|MSIL yönergeleri|Kodunuzu oluşturan Microsoft ara dili (MSIL) yönergeleri. Birçok MSIL yönergesi metaveri belirteçleri ile birlikte bulunur.|
|Meta Veriler|Metaveri tabloları ve yığınlar Çalışma zamanı, bu bölümü, kodunuzdaki tüm türler ve üyeler hakkında bilgi kaydetmek için kullanır. Bu bölüm ayrıca özel öznitelikler ve güvenlik bilgileri de içerir.|

## <a name="run-time-use-of-metadata"></a>Meta Verilerin Çalışma Zamanında Kullanımı

Meta veri ve ortak dil çalışma zamanı rolüne daha iyi anlamak için basit bir program oluşturmak ve meta veri çalışma zamanı ömrü nasıl etkilediğini göstermek faydalı olabilir. Aşağıdaki kod örneğinde adlı bir sınıf içinde iki yöntemi gösterilir `MyApp`. `Main` Yöntemdir programın giriş noktası sırada `Add` yöntemi yalnızca iki tamsayı bağımsız değişkenleri toplamını döndürür.

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

Kod çalıştığında, çalışma zamanı modülü belleğine yükler ve bu sınıf için meta veriler danışır. Veriler yüklendikten sonra çalışma zamanı kapsamlı hızlı yerel makine yönergelerine dönüştürmek için yöntemin Microsoft Ara dili (MSIL) akış analizini yapar. Çalışma zamanı, just-ın-time (JIT) derleyici MSIL yönergeleri gerektiği gibi aynı anda yerel makine koduna bir yönteme dönüştürmek için kullanır.

Önceki kodun üretilen MSIL bölümü aşağıdaki örnekte `Main` işlevi. MSIL ve meta verileri, tüm .NET Framework kullanarak uygulama görüntüleyebileceğiniz [MSIL Disassembler (Ildasm.exe)](../../docs/framework/tools/ildasm-exe-il-disassembler.md).

```
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

JIT derleyicisi, tüm yöntem için MSIL kapsamlı olarak analiz eder ve verimli yerel yönergeler yöntemi oluşturur okur. Konumunda `IL_000d`, bir metaveri belirteci için `Add` yöntemi (`/*` `06000003 */`) karşılaşılırsa ve çalışma zamanı, üçüncü satır başvurmanız belirtecini kullanır. **MethodDef** tablo.

Aşağıdaki tabloda gösterilmektedir parçası **MethodDef** açıklayan meta veri belirteci tarafından başvurulan tablo `Add` yöntemi. Yalnızca bu tablo, diğer meta veri tablolarını bu derlemede var ve kendi benzersiz değerlere sahip olsa da ele alınmıştır.

|Satır|Göreli sanal adres (RVA)|ImplFlags|Bayraklar|Ad<br /><br /> (Dize yığın işaret.)|İmza (yığın BLOB işaret eder.)|
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|
|1.|0x00002050|IL<br /><br /> Yönetilen|Ortak<br /><br /> ReuseSlot<br /><br /> SpecialName<br /><br /> RTSpecialName<br /><br /> .ctor|.ctor (oluşturucu)||
|2|0x00002058|IL<br /><br /> Yönetilen|Ortak<br /><br /> Statik<br /><br /> ReuseSlot|Ana|Dize|
|3|0x0000208c|IL<br /><br /> Yönetilen|Ortak<br /><br /> Statik<br /><br /> ReuseSlot|Ekle|int, int, int|

Tablonun her sütunu kodunuz hakkında önemli bilgiler içerir. **RVA** sütun, bu yöntem tanımlar MSIL başlangıç bellek adresi hesaplamak çalışma zamanı sağlar. **ImplFlags** ve **bayrakları** sütunları içerir (örneğin, yöntem genel veya özel olup) yöntemi açıklayan bir bit maskesi. **Adı** sütun dizinleri dize yığınında metodun adı. **İmza** sütun, yöntemin imzası blob yığınındaki tanımını dizinler.

Çalışma zamanı istenen uzaklık adresinden hesaplar **RVA** üçüncü satırda sütun ve sonra yeni adresine geçer ve JIT derleyicisi bu adresi döndürür. JIT derleyicisi, başka bir meta veri belirteci karşılaşır ve işlem yinelenir kadar yeni adresindeki MSIL işlemeye devam eder.

Meta verileri kullanarak, çalışma zamanı kodunuzu yükle ve yerel makine yönergelerine işlemek gerekli tüm bilgilere erişebilir. Bu şekilde, kendiliğinden açıklayıcı dosyalar meta veri sağlar ve ortak tür sistemi, diller arası devralma birlikte.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Öznitelikler](../../docs/standard/attributes/index.md)|Öznitelikleri uygulama, özel öznitelikler yazma ve özniteliklerde depolanan bilgileri alma açıklar.|
