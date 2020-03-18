---
title: "İzim: Visual Studio'da yönetilen derlemelerden türleri gömme"
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: f11fbedad766753ee462c5f597b823493cdaf7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75338553"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a>İzim: Visual Studio'da yönetilen derlemelerden türleri gömme

Güçlü adlandırılmış yönetilen bir derlemeden tür bilgilerini katıştırmak, sürüm bağımsızlığı elde etmek için bir uygulamada gevşek çift türleri yapabilirsiniz. Diğer bir diğer olarak, programınız, her yeni sürüm için yeniden derlenmek zorunda kalmadan yönetilen kitaplığın herhangi bir sürümünden türleri kullanmak üzere yazılabilir.

Tür katıştırma, Microsoft Office'in otomasyon nesnelerini kullanan bir uygulama gibi COM interop'uyla sıklıkla kullanılır. Tür bilgilerini katıştırma, bir programın aynı yapısının farklı bilgisayarlarda Microsoft Office'in farklı sürümleriyle çalışmasını sağlar. Ancak, tam olarak yönetilen çözümlerle tür katıştırma da kullanabilirsiniz.

Katıştırılmış ortak arabirimleri belirttikten sonra, bu arabirimleri uygulayan çalışma zamanı sınıfları oluşturursunuz. İstemci programı, ortak arabirimleri içeren derlemeye başvurarak ve başvurunun özelliğini `Embed Interop Types` ayarlayarak, arabirimlerin tür `True`bilgilerini tasarım zamanında katıştırabilir. İstemci programı daha sonra bu arabirimler olarak yazılan çalışma zamanı nesnelerinin örneklerini yükleyebilir. Bu komut satırı derleyicisi kullanarak ve [-link derleyici seçeneği](../../csharp/language-reference/compiler-options/link-compiler-option.md)kullanarak derleme başvuru eşdeğerdir.

Güçlü adlandırılmış çalışma zamanı derlemenizin yeni bir sürümünü oluşturursanız, istemci programının yeniden derlenmesine gerek yoktur. İstemci programı, ortak arabirimler için katıştırılmış tür bilgilerini kullanarak, çalışma zamanı derlemesinin hangi sürümünü kullanabilirse kullanmaya devam eder.

Bu gözden geçirmede, siz:

1. Katıştırılmış tür bilgilerini içeren ortak arabirimiçeren güçlü adlandırılmış bir derleme oluşturun.
1. Ortak arabirimi uygulayan güçlü adlandırılmış bir çalışma zamanı derlemesi oluşturun.
1. Ortak arabirimden tür bilgilerini gömen ve çalışma zamanı derlemesinden sınıfın bir örneğini oluşturan bir istemci programı oluşturun.
1. Çalışma zamanı montajını değiştirin ve yeniden oluşturun.
1. Yeniden derlenmek zorunda kalmadan çalışma zamanı derlemesinin yeni sürümünü kullandığını görmek için istemci programını çalıştırın.

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a>Koşullar ve sınırlamalar

Bir derlemeden tür bilgilerini aşağıdaki koşullar altında katıştırabilirsiniz:

- Derleme, en az bir ortak arabirimi ortaya çıkarır.
- Katıştılı arabirimler, benzersiz `ComImport` GUID'lere sahip öznitelikler ve `Guid` özniteliklerle açıklamalı olarak açıklanır.
- Derleme öznitelik veya `ImportedFromTypeLib` `PrimaryInteropAssembly` öznitelik ve derleme düzeyinde `Guid` öznitelik ile açıklamalı. Visual C# ve Visual Basic proje şablonları `Guid` varsayılan olarak montaj düzeyinde bir öznitelik içerir.

Tür katıştırma birincil işlevi COM interop derlemeleri desteklemek olduğundan, tam yönetilen bir çözüme tür bilgilerini katıştırdığınızda aşağıdaki sınırlamalar geçerlidir:

- Yalnızca COM interop'a özgü öznitelikler gömülür. Diğer öznitelikler yoksayılır.
- Bir tür genel parametreler kullanıyorsa ve genel parametre türü katıştırılmış bir türse, bu tür derleme sınırı boyunca kullanılamaz. Derleme sınırını aşmaya örnek olarak yöntem başka bir derlemeden çağrı veya başka bir derlemede tanımlanan bir türden tür elde etmek verilebilir.
- Sabitler gömülü değildir.
- Sınıf, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> anahtar olarak katışılmış bir türü desteklemez. Katıştırılmış bir türü anahtar olarak desteklemek için kendi sözlük türünüzü uygulayabilirsiniz.

## <a name="create-an-interface"></a>Arayüz oluşturma

İlk adım türü eşdeğerlik arabirim derlemeoluşturmaktır.

1. Visual Studio'da **Dosya** > **Yeni** > **Projesi'ni**seçin.

1. Yeni **proje** iletişim kutusu oluştur kutusunda, **şablonları ara** kutusuna *sınıf kitaplığı* yazın. Listeden C# veya Visual Basic **Class Library (.NET Framework)** şablonu seçin ve sonra **İleri'yi**seçin.

1. Yeni proje iletişim **kutunuzu Yapıla,** **Proje adı**altında , *TypeEquivalenceInterface*yazın ve ardından **Oluştur'u**seçin. Yeni proje oluşturuldu.

1. **Solution Explorer'da** *Class1.cs* veya *Class1.vb* dosyasına sağ tıklayın, **Yeniden Adlandır'ı**seçin ve dosyayı *Class1'den* *ISampleInterface'e*yeniden adlandırın. Sınıfı yeniden adlandırmak için istem `ISampleInterface`için **Evet'i** yanıtlayın. Bu sınıf, sınıfın ortak arabirimini temsil eder.

1. **Solution Explorer'da** **TypeEquivalenceInterface** projesini sağ tıklatın ve ardından **Özellikler'i**seçin.

1. **Özellikler** ekranının sol bölmesine **Yap'ı** seçin ve **Çıktı yolunu** *bilgisayarınızdaki C:\TypeEquivalenceSample*gibi bir konuma ayarlayın. Bu yol boyunca aynı konumu kullanırsınız.

1. **Özellikler** ekranının sol bölmesine **İmzala'yı** seçin ve ardından montaj onay kutusunu **imzala'yı** seçin. **Güçlü bir ad tuşu dosyası seç**için açılan açılır durumda Yeni'yi seçin. **New**

1. Güçlü **Ad Anahtarı Oluştur** iletişim kutusunda, **Anahtar dosya adı**altında , *key.snk*yazın. Parola onay **kutusuyla anahtar dosyamı koruyun'un** select'ini seçin ve ardından **Tamam'ı**seçin.

1. Kod düzenleyicisinde *ISampleInterface* sınıf dosyasını açın ve arabirimi oluşturmak `ISampleInterface` için içeriğini aşağıdaki kodla değiştirin:

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   namespace TypeEquivalenceInterface
   {
       [ComImport]
       [Guid("8DA56996-A151-4136-B474-32784559F6DF")]
       public interface ISampleInterface
       {
           void GetUserInput();
           string UserInput { get; }
       }
   }
   ```

   ```vb
   Imports System.Runtime.InteropServices

   <ComImport()>
   <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
   Public Interface ISampleInterface
       Sub GetUserInput()
       ReadOnly Property UserInput As String
   End Interface
   ```

1. **Araçlar** menüsünde **Guid Oluştur'u**ve **GUID Oluştur** iletişim kutusunda Kayıt **Defteri Biçimi'ni**seçin. **Kopyala'yı**seçin ve ardından **Çıkış'ı**seçin.

1. Kodunuzu `Guid` öznitelik olarak, örnek GUID'i kopyaladiğiniz GUID ile değiştirin ve ayraçları kaldırın (**{ }**).

1. **Solution Explorer'da** **Özellikler** klasörünü genişletin ve *AssemblyInfo.cs* veya *AssemblyInfo.vb* dosyasını seçin. Kod düzenleyicisinde, dosyaya aşağıdaki özniteliği ekleyin:

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. **Dosyaları** > ve projeyi kaydetmek için Dosya**Tümünü Kaydet'i** seçin veya **Ctrl**+**Shift**+**S** tuşuna basın.

1. **Solution Explorer'da** **TypeEquivalenceInterface** projesini sağ tıklatın ve **Oluştur'u**seçin. Sınıf kitaplığı DLL dosyası derlenir ve belirtilen yapı çıktı yoluna kaydedilir, örneğin *C:\TypeEquivalenceSample*.

## <a name="create-a-runtime-class"></a>Çalışma zamanı sınıfı oluşturma

Ardından, tür eşdeğerliği çalışma zamanı sınıfını oluşturun.

1. Visual Studio'da **Dosya** > **Yeni** > **Projesi'ni**seçin.

1. Yeni **proje** iletişim kutusu oluştur kutusunda, **şablonları ara** kutusuna *sınıf kitaplığı* yazın. Listeden C# veya Visual Basic **Class Library (.NET Framework)** şablonu seçin ve sonra **İleri'yi**seçin.

1. Yeni proje iletişim **kutunuzu Yapıla,** **Proje adı**altında , *TypeEquivalenceRuntime*yazın ve ardından **Oluştur'u**seçin. Yeni proje oluşturuldu.

1. **Çözüm Gezgini'nde,** *Class1.cs* veya *Class1.vb* dosyasına sağ tıklayın, **Yeniden Adlandır'ı**seçin ve dosyayı *Class1'den* *SampleClass'a*yeniden adlandırın. Sınıfı yeniden adlandırmak için istem `SampleClass`için **Evet'i** yanıtlayın. Bu sınıf `ISampleInterface` arabirimi uygular.

1. **Solution Explorer'da** **TypeEquivalenceInterface** projesini sağ tıklatın ve **Özellikleri**seçin.

1. **Özellikler** ekranının sol bölmesine **Yapı'yı** seçin ve çıktı **yolunu** TypeEquivalenceInterface projesi için kullandığınız konuma ayarlayın, örneğin *C:\TypeEquivalenceSample*.

1. **Özellikler** ekranının sol bölmesine **İmzala'yı** seçin ve ardından montaj onay kutusunu **imzala'yı** seçin. **Güçlü bir ad tuşu dosyası seç**için açılan açılır durumda Yeni'yi seçin. **New**

1. Güçlü **Ad Anahtarı Oluştur** iletişim kutusunda, **Anahtar dosya adı**altında , *key.snk*yazın. Parola onay **kutusuyla anahtar dosyamı koruyun'un** select'ini seçin ve ardından **Tamam'ı**seçin.

1. **Çözüm Gezgini'nde** **TypeEquivalenceRuntime** projesine sağ tıklayın ve**Referans** **Ekle'yi** > seçin.

1. Başvuru **Yöneticisi** iletişim kutusunda **Gözat'ı** seçin ve çıktı yolu klasörüne göz atın. *TypeEquivalenceInterface.dll* dosyasını seçin, **Ekle'yi**seçin ve ardından **Tamam'ı**seçin.

1. **Solution**Explorer'da, **Başvurular** klasörünü genişletin ve **TypeEquivalenceInterface** başvurualanını seçin. **Özellikler** bölmesinde, zaten değilse **Belirli Sürümü** **False** olarak ayarlayın.

1. Kod düzenleyicisinde *SampleClass* sınıf dosyasını açın ve sınıfı oluşturmak için `SampleClass` içeriğini aşağıdaki kodla değiştirin:

   ```csharp
   using System;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceRuntime
   {
       public class SampleClass : ISampleInterface
       {
           private string p_UserInput;
           public string UserInput { get { return p_UserInput; } }

           public void GetUserInput()
           {
               Console.WriteLine("Please enter a value:");
               p_UserInput = Console.ReadLine();
           }
       }
   }
   ```

   ```vb
   Imports TypeEquivalenceInterface

   Public Class SampleClass
       Implements ISampleInterface

       Private p_UserInput As String
       Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput
           Get
               Return p_UserInput
           End Get
       End Property

       Public Sub GetUserInput() Implements ISampleInterface.GetUserInput
           Console.WriteLine("Please enter a value:")
           p_UserInput = Console.ReadLine()
       End Sub
   End Class
   ```

1. **Dosyaları** > ve projeyi kaydetmek için Dosya**Tümünü Kaydet'i** seçin veya **Ctrl**+**Shift**+**S** tuşuna basın.

1. **Çözüm Gezgini'nde** **TypeEquivalenceRuntime** projesini sağ tıklatın ve **Build'i**seçin. Sınıf kitaplığı DLL dosyası derlenir ve belirtilen yapı çıktı yoluna kaydedilir.

## <a name="create-a-client-project"></a>İstemci projesi oluşturma

Son olarak, arabirim derlemesine başvuran bir tür eşdeğerlik istemci programı oluşturun.

1. Visual Studio'da **Dosya** > **Yeni** > **Projesi'ni**seçin.

1. Yeni **bir proje** oluştur iletişim kutusunda **şablonara** kutusuna *konsol* yazın. Listeden C# veya Visual Basic **Console App (.NET Framework)** şablonundan birini seçin ve ardından **İleri'yi**seçin.

1. Yeni proje iletişim **kutunuzu Yapıla,** **Proje adı altında**, *TypeEquivalenceClient*yazın ve ardından **Oluştur'u**seçin. Yeni proje oluşturuldu.

1. **Çözüm Gezgini'nde** **TypeEquivalenceClient** projesini sağ tıklatın ve **Özellikler'i**seçin.

1. **Özellikler** ekranının sol bölmesine **Yapı'yı** seçin ve çıktı **yolunu** TypeEquivalenceInterface projesi için kullandığınız konuma ayarlayın, örneğin *C:\TypeEquivalenceSample*.

1. **Çözüm Gezgini'nde** **TypeEquivalenceClient** projesine sağ tıklayın ve**Referans** **Ekle'yi** > seçin.

1. Başvuru **Yöneticisi** iletişim kutusunda, **TypeEquivalenceInterface.dll** dosyası zaten listelenmişse, bu dosyayı seçin. Değilse, **Gözat**seçin , çıkış yolu klasörüne göz atın, *TypeEquivalenceInterface.dll* dosyasını seçin *(TypeEquivalenceRuntime.dll*değil), ve **Ekle**seçin . **Tamam'ı**seçin.

1. **Solution**Explorer'da, **Başvurular** klasörünü genişletin ve **TypeEquivalenceInterface** başvurualanını seçin. **Özellikler** bölmesinde, **Embed Interop Türlerini** **True**olarak ayarlayın.

1. Kod düzenleyicisindeki *Program.cs* veya *Module1.vb* dosyasını açın ve istemci programını oluşturmak için içeriğini aşağıdaki kodla değiştirin:

   ```csharp
   using System;
   using System.Reflection;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceClient
   {
       class Program
       {
           static void Main(string[] args)
           {
               Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");
               ISampleInterface sampleClass =
                   (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");
               sampleClass.GetUserInput();
               Console.WriteLine(sampleClass.UserInput);
               Console.WriteLine(sampleAssembly.GetName().Version.ToString());
               Console.ReadLine();
           }
       }
   }
   ```

   ```vb
   Imports System.Reflection
   Imports TypeEquivalenceInterface

   Module Module1

       Sub Main()
           Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")
           Dim sampleClass As ISampleInterface = CType( _
               sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)
           sampleClass.GetUserInput()
           Console.WriteLine(sampleClass.UserInput)
           Console.WriteLine(sampleAssembly.GetName().Version)
           Console.ReadLine()
       End Sub

   End Module
   ```

1. **Dosyaları** > ve projeyi kaydetmek için Dosya**Tümünü Kaydet'i** seçin veya **Ctrl**+**Shift**+**S** tuşuna basın.

1. Programı oluşturmak ve çalıştırmak için **Ctrl**+**F5** tuşuna basın. Konsol çıkışının montaj sürümünü **1.0.0.0**döndürür.

## <a name="modify-the-interface"></a>Arabirimi değiştirme

Şimdi, arabirim montajını değiştirin ve sürümünü değiştirin.

1. Visual Studio'da **Dosya** > **Açık** > **Projesi/Çözümü'nü**seçin ve **TypeEquivalenceInterface** projesini açın.

1. **Solution Explorer'da** **TypeEquivalenceInterface** projesini sağ tıklatın ve **Özellikleri**seçin.

1. **Özellikler** ekranının sol bölmesine **Uygulama'yı** seçin ve ardından **Derleme Bilgileri'ni**seçin.

1. Derleme **Bilgileri** iletişim kutusunda, **Derleme sürümü** ve Dosya **sürüm** değerlerini *2.0.0.0*olarak değiştirin ve ardından **Tamam'ı**seçin.

1. *SampleInterface.cs* veya *SampleInterface.vb* dosyasını açın ve arabirime `ISampleInterface` aşağıdaki kod satırını ekleyin:

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. **Dosyaları** > ve projeyi kaydetmek için Dosya**Tümünü Kaydet'i** seçin veya **Ctrl**+**Shift**+**S** tuşuna basın.

1. **Solution Explorer'da** **TypeEquivalenceInterface** projesini sağ tıklatın ve **Oluştur'u**seçin. Sınıf kitaplığı DLL dosyasının yeni bir sürümü derlenir ve yapı çıktı yoluna kaydedilir.

## <a name="modify-the-runtime-class"></a>Çalışma zamanı sınıfını değiştirme

Ayrıca çalışma zamanı sınıfını değiştirin ve sürümünü güncelleştirin.

1. Visual Studio'da **Dosya** > **Açık** > **Projesi/Çözümü'nü**seçin ve **TypeEquivalenceRuntime** projesini açın.

1. **Çözüm Gezgini'nde** **TypeEquivalenceRuntime** projesini sağ tıklatın ve **Özellikleri**seçin.

1. **Özellikler** ekranının sol bölmesine **Uygulama'yı** seçin ve ardından **Derleme Bilgileri'ni**seçin.

1. Derleme **Bilgileri** iletişim kutusunda, **Derleme sürümü** ve Dosya **sürüm** değerlerini *2.0.0.0*olarak değiştirin ve ardından **Tamam'ı**seçin.

1. *SampleClass.cs* veya *SampleClass.vb* dosyasını `SampleClass` açın ve sınıfa aşağıdaki kodu ekleyin:

   ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
   ```

   ```vb
   Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
       Return Now
   End Function
   ```

1. **Dosyaları** > ve projeyi kaydetmek için Dosya**Tümünü Kaydet'i** seçin veya **Ctrl**+**Shift**+**S** tuşuna basın.

1. **Çözüm Gezgini'nde** **TypeEquivalenceRuntime** projesini sağ tıklatın ve **Build'i**seçin. Sınıf kitaplığı DLL dosyasının yeni bir sürümü derlenir ve yapı çıktı yoluna kaydedilir.

## <a name="run-the-updated-client-program"></a>Güncelleştirilmiş istemci programını çalıştırın

Yapı çıktı klasörü konumuna gidin ve *TypeEquivalenceClient.exe'yi*çalıştırın. Konsol çıkışının artık `TypeEquivalenceRuntime` derlemenin yeni sürümünü yansıttığını unutmayın, *2.0.0.0*, program yeniden derlenmeden.

## <a name="see-also"></a>Ayrıca bkz.

- [-link (C# Derleyici Seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-bağlantı (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
- [C# programlama kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
