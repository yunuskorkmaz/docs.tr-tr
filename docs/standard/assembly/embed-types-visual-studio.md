---
title: 'İzlenecek yol: Visual Studio’da yönetilen bütünleştirilmiş kodlardan türleri ekleme'
description: Bu izlenecek yol, Visual Studio kullanarak .NET 'teki yönetilen derlemelerden türlerin nasıl ekleneceğini gösterir. Gömülü türler, sürüm bağımsızlığını destekleyebilir.
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 636e5f8095b64cd0f445555c96d00945ccf7eaf8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378979"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a>İzlenecek yol: Visual Studio’da yönetilen bütünleştirilmiş kodlardan türleri ekleme

Tanımlayıcı adlı yönetilen bir derlemeden tür bilgilerini eklerseniz, sürüm bağımsızlığını elde etmek için bir uygulamada gevşek olarak birkaç tür oluşturabilirsiniz. Diğer bir deyişle, programınız her yeni sürüm için yeniden derlenmesi gerekmeden yönetilen bir kitaplığın herhangi bir sürümündeki türleri kullanmak üzere yazılabilir.

Tür ekleme, genellikle Microsoft Office Otomasyon nesneleri kullanan bir uygulama gibi COM birlikte çalışma ile kullanılır. Tür bilgilerinin gömülmesi, farklı bilgisayarlarda farklı Microsoft Office sürümleriyle çalışmak için aynı programın derlemesini sağlar. Ancak, tam olarak yönetilen çözümlerle tür eklemeyi de kullanabilirsiniz.

Katıştırılabilen ortak arabirimleri belirttikten sonra, bu arabirimleri uygulayan çalışma zamanı sınıfları oluşturursunuz. İstemci programı, genel arabirimleri içeren derlemeye başvurarak ve başvurusunun özelliğini ayarlayarak, tasarım zamanında arabirimlerin tür bilgilerini ekleyebilir `Embed Interop Types` `True` . İstemci programı daha sonra bu arabirimler olarak yazılmış çalışma zamanı nesnelerinin örneklerini yükleyebilir. Bu, komut satırı derleyicisini kullanmakla ve derlemeye, [-Link derleyici seçeneği](../../csharp/language-reference/compiler-options/link-compiler-option.md)kullanılarak başvurulmaya eşdeğerdir.

Güçlü adlandırılmış çalışma zamanı derlemenin yeni bir sürümünü oluşturursanız, istemci programın yeniden derlenmesi gerekmez. İstemci programı, ortak arabirimler için katıştırılmış tür bilgilerini kullanarak çalışma zamanı derlemesinin hangi sürümünün kullanılabilir olduğunu kullanmaya devam eder.

Bu izlenecek yolda şunları yapabilirsiniz:

1. Katıştırılabilen tür bilgilerini içeren bir ortak arabirim ile tanımlayıcı adlı bir derleme oluşturun.
1. Ortak arabirimi uygulayan, tanımlayıcı adlı bir çalışma zamanı derlemesi oluşturun.
1. Ortak arabirimden tür bilgilerini katıştıran bir istemci programı oluşturun ve çalışma zamanı derlemesinden sınıfın bir örneğini oluşturur.
1. Çalışma zamanı derlemesini değiştirin ve yeniden derleyin.
1. Yeniden derlenmesi gerekmeden, çalışma zamanı derlemesinin yeni sürümünü kullandığını görmek için istemci programını çalıştırın.

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a>Koşullar ve sınırlamalar

Bir derlemeden tür bilgilerini aşağıdaki koşullarda ekleyebilirsiniz:

- Derleme en az bir ortak arabirim kullanıma sunar.
- Katıştırılmış arabirimlere, `ComImport` `Guid` benzersiz GUID 'leri olan öznitelikler ve özniteliklerle açıklama eklenir.
- Derlemeye, `ImportedFromTypeLib` özniteliğiyle veya `PrimaryInteropAssembly` özniteliğiyle ve derleme düzeyi özniteliğiyle açıklama eklenir `Guid` . Visual C# ve Visual Basic proje şablonları varsayılan olarak bir derleme düzeyi `Guid` özniteliği içerir.

Ekleme türü birincil işlevi COM birlikte çalışma derlemelerini desteklemek olduğundan, tür bilgilerini tam olarak yönetilen bir çözüme eklediğinizde aşağıdaki sınırlamalar geçerlidir:

- Yalnızca COM birlikte çalışabilirliğine özgü öznitelikler katıştırılır. Diğer öznitelikler yok sayılır.
- Bir tür genel parametreler kullanıyorsa ve genel parametrenin türü gömülü bir türse, bu tür bir derleme sınırı boyunca kullanılamaz. Bir derleme sınırının geçmesinin örnekleri, başka bir derlemeden bir yöntemi çağırmayı veya başka bir derlemede tanımlanan türden bir tür türetmeyi içerir.
- Sabitler ekli değil.
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>Sınıf, gömülü bir türü anahtar olarak desteklemez. Gömülü bir türü anahtar olarak desteklemek için kendi sözlük türünü uygulayabilirsiniz.

## <a name="create-an-interface"></a>Arabirim oluşturma

İlk adım tür denklik arabirim derlemesini oluşturmaktır.

1. Visual Studio 'da **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

1. **Yeni proje oluştur** iletişim kutusunda, **şablon ara** kutusuna *sınıf kitaplığı* yazın. Listeden C# veya Visual Basic **Class Library (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.

1. **Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı**altında *TypeEquivalenceInterface*yazın ve ardından **Oluştur**' u seçin. Yeni proje oluşturulur.

1. **Çözüm Gezgini**' de, *Class1.cs* veya *Class1. vb* dosyasını sağ tıklatın, **Yeniden Adlandır**' ı seçin ve dosyayı SınıfAdı SınıfAdı *' dan* *isampelınterface*olarak yeniden adlandırın. Ayrıca sınıfını olarak yeniden adlandırmak için istemine **Evet** yanıtı verin `ISampleInterface` . Bu sınıf, sınıfının genel arabirimini temsil eder.

1. **Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve ardından **Özellikler**' i seçin.

1. **Özellikler** ekranının sol bölmesinde **Oluştur** ' u seçin ve **Çıkış yolunu** bilgisayarınızdaki bir konuma (örneğin, *C:\TypeEquivalenceSample*) ayarlayın. Bu izlenecek yol boyunca aynı konumu kullanırsınız.

1. **Özellikler** ekranının sol bölmesinde **oturum** aç ' ı seçin ve ardından **derlemeyi imzala** onay kutusunu seçin. **Bir tanımlayıcı ad anahtar dosyası seç**açılan menüsünde **Yeni**' yi seçin.

1. **Tanımlayıcı ad anahtarı oluştur** iletişim kutusunda, **anahtar dosya adı**altında *Key. snk*yazın. **Anahtar dosyamı parolayla koru** onay kutusunu kaldırın ve ardından **Tamam**' ı seçin.

1. Kod düzenleyicisinde *ısamptaınterface* sınıf dosyasını açın ve aşağıdaki kodla içeriğini değiştirerek `ISampleInterface` arabirimi oluşturun:

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

1. **Araçlar** menüsünde **GUID oluştur**' u seçin ve **Guid oluştur** iletişim kutusunda **kayıt defteri biçimi**' ni seçin. **Kopyala**' yı seçin ve ardından **Çıkış**' ı seçin.

1. `Guid`Kodunuzun özniteliğinde, örnek GUID 'yi KOPYALADıĞıNıZ GUID ile değiştirin ve ayraçları (**{}**) kaldırın.

1. **Çözüm Gezgini**, **Özellikler** klasörünü genişletin ve *AssemblyInfo.cs* veya *AssemblyInfo. vb* dosyasını seçin. Kod Düzenleyicisi 'nde, dosyaya aşağıdaki özniteliği ekleyin:

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. **Dosya**  >  **Save All** **Ctrl** + **Shift** + **S** ve proje kaydetmek için Tümünü Kaydet ' i seçin veya CTRL SHIFT 'e basın.

1. **Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve **Oluştur**' u seçin. Sınıf kitaplığı DLL dosyası derlenir ve belirtilen derleme çıkış yoluna kaydedilir, örneğin *C:\TypeEquivalenceSample*.

## <a name="create-a-runtime-class"></a>Çalışma zamanı sınıfı oluşturma

Sonra, tür eşdeğerlik çalışma zamanı sınıfını oluşturun.

1. Visual Studio 'da **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

1. **Yeni proje oluştur** iletişim kutusunda, **şablon ara** kutusuna *sınıf kitaplığı* yazın. Listeden C# veya Visual Basic **Class Library (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.

1. **Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı**altında *TypeEquivalenceRuntime*yazın ve ardından **Oluştur**' u seçin. Yeni proje oluşturulur.

1. **Çözüm Gezgini**, *Class1.cs* veya *Class1. vb* dosyasını sağ tıklayın, **Yeniden Adlandır**' ı seçin ve dosyayı *SınıfAdı SınıfAdı* *' dan* SampleClass olarak yeniden adlandırın. Ayrıca sınıfını olarak yeniden adlandırmak için istemine **Evet** yanıtı verin `SampleClass` . Bu sınıf, `ISampleInterface` arabirimini uygular.

1. **Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve **Özellikler**' i seçin.

1. **Özellikler** ekranının sol bölmesinde **Oluştur** ' u seçin ve ardından **Çıkış yolunu** TypeEquivalenceInterface projesi için kullandığınız aynı konuma ayarlayın, örneğin, *C:\TypeEquivalenceSample*.

1. **Özellikler** ekranının sol bölmesinde **oturum** aç ' ı seçin ve ardından **derlemeyi imzala** onay kutusunu seçin. **Bir tanımlayıcı ad anahtar dosyası seç**açılan menüsünde **Yeni**' yi seçin.

1. **Tanımlayıcı ad anahtarı oluştur** iletişim kutusunda, **anahtar dosya adı**altında *Key. snk*yazın. **Anahtar dosyamı parolayla koru** onay kutusunu kaldırın ve ardından **Tamam**' ı seçin.

1. **Çözüm Gezgini**, **TypeEquivalenceRuntime** projesine sağ tıklayın ve başvuru **Ekle**' yi seçin  >  **Reference**.

1. **Başvuru Yöneticisi** iletişim kutusunda, **Araştır** ' ı seçin ve çıkış yolu klasörüne gidin. *TypeEquivalenceInterface. dll* dosyasını seçin, **Ekle**' yi seçin ve ardından **Tamam**' ı seçin.

1. **Çözüm Gezgini**, **Başvurular** klasörünü genişletin ve **TypeEquivalenceInterface** başvurusunu seçin. **Özellikler** bölmesinde, **belirli bir sürümü** henüz yoksa **yanlış** olarak ayarlayın.

1. Kod düzenleyicisinde *SampleClass* sınıf dosyasını açın ve sınıfını oluşturmak için içeriğini aşağıdaki kodla değiştirin `SampleClass` :

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

1. **Dosya**  >  **Save All** **Ctrl** + **Shift** + **S** ve proje kaydetmek için Tümünü Kaydet ' i seçin veya CTRL SHIFT 'e basın.

1. **Çözüm Gezgini**, **TypeEquivalenceRuntime** projesine sağ tıklayın ve **Oluştur**' u seçin. Sınıf kitaplığı DLL dosyası derlenir ve belirtilen yapı çıkış yoluna kaydedilir.

## <a name="create-a-client-project"></a>İstemci projesi oluşturma

Son olarak, arabirim derlemesine başvuran bir tür denklik istemci programı oluşturun.

1. Visual Studio 'da **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

1. **Yeni proje oluştur** iletişim kutusunda, **şablon ara** kutusuna *konsol* yazın. Listeden C# veya Visual Basic **konsol uygulaması (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.

1. **Yeni projenizi yapılandırın** iletişim kutusunda, **Proje adı**altında *TypeEquivalenceClient*yazın ve ardından **Oluştur**' u seçin. Yeni proje oluşturulur.

1. **Çözüm Gezgini**, **TypeEquivalenceClient** projesine sağ tıklayın ve **Özellikler**' i seçin.

1. **Özellikler** ekranının sol bölmesinde **Oluştur** ' u seçin ve ardından **Çıkış yolunu** TypeEquivalenceInterface projesi için kullandığınız aynı konuma ayarlayın, örneğin, *C:\TypeEquivalenceSample*.

1. **Çözüm Gezgini**, **TypeEquivalenceClient** projesine sağ tıklayın ve başvuru **Ekle**' yi seçin  >  **Reference**.

1. **Başvuru Yöneticisi** iletişim kutusunda, **TypeEquivalenceInterface. dll** dosyası zaten listeleniyorsa, onu seçin. Aksi takdirde, **Araştır**' ı seçin, çıkış yolu klasörüne gidin, *TypeEquivalenceInterface. dll* dosyasını ( *TypeEquivalenceRuntime. dll*değil) seçin ve **Ekle**' yi seçin. **Tamam**’ı seçin.

1. **Çözüm Gezgini**, **Başvurular** klasörünü genişletin ve **TypeEquivalenceInterface** başvurusunu seçin. **Özellikler** bölmesinde, **birlikte çalışma türlerini katıştır** ' ı **doğru**olarak ayarlayın.

1. Kod düzenleyicisinde *program.cs* veya *Module1. vb* dosyasını açın ve istemci programını oluşturmak için içeriğini aşağıdaki kodla değiştirin:

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

1. **Dosya**  >  **Save All** **Ctrl** + **Shift** + **S** ve proje kaydetmek için Tümünü Kaydet ' i seçin veya CTRL SHIFT 'e basın.

1. **Ctrl** + Programı derlemek ve çalıştırmak için CTRL**F5** tuşuna basın. Konsol çıkışının **1.0.0.0**derleme sürümünü döndürdüğünü unutmayın.

## <a name="modify-the-interface"></a>Arabirimi değiştirme

Şimdi, arabirim derlemesini değiştirin ve sürümünü değiştirin.

1. Visual Studio 'da **Dosya**  >  **Aç**  >  **Proje/çözüm**' ü seçin ve **TypeEquivalenceInterface** projesini açın.

1. **Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve **Özellikler**' i seçin.

1. **Özellikler** ekranının sol bölmesinde **uygulama** ' yı seçin ve ardından **derleme bilgileri**' ni seçin.

1. **Derleme bilgileri** Iletişim kutusunda **derleme sürümünü** ve **dosya sürümü** değerlerini *2.0.0.0*olarak değiştirip **Tamam**' ı seçin.

1. *SampleInterface.cs* veya *sampleınterface. vb* dosyasını açın ve aşağıdaki kod satırını `ISampleInterface` arabirime ekleyin:

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. **Dosya**  >  **Save All** **Ctrl** + **Shift** + **S** ve proje kaydetmek için Tümünü Kaydet ' i seçin veya CTRL SHIFT 'e basın.

1. **Çözüm Gezgini**, **TypeEquivalenceInterface** projesine sağ tıklayın ve **Oluştur**' u seçin. Sınıf kitaplığı DLL dosyasının yeni bir sürümü derlenir ve derleme çıkış yoluna kaydedilir.

## <a name="modify-the-runtime-class"></a>Çalışma zamanı sınıfını değiştirme

Ayrıca çalışma zamanı sınıfını değiştirin ve sürümünü güncelleştirin.

1. Visual Studio 'da **Dosya**  >  **Aç**  >  **Proje/çözüm**' ü seçin ve **TypeEquivalenceRuntime** projesini açın.

1. **Çözüm Gezgini**, **TypeEquivalenceRuntime** projesine sağ tıklayın ve **Özellikler**' i seçin.

1. **Özellikler** ekranının sol bölmesinde **uygulama** ' yı seçin ve ardından **derleme bilgileri**' ni seçin.

1. **Derleme bilgileri** Iletişim kutusunda **derleme sürümünü** ve **dosya sürümü** değerlerini *2.0.0.0*olarak değiştirip **Tamam**' ı seçin.

1. *SampleClass.cs* veya *SampleClass. vb* dosyasını açın ve sınıfına aşağıdaki kodu ekleyin `SampleClass` :

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

1. **Dosya**  >  **Save All** **Ctrl** + **Shift** + **S** ve proje kaydetmek için Tümünü Kaydet ' i seçin veya CTRL SHIFT 'e basın.

1. **Çözüm Gezgini**, **TypeEquivalenceRuntime** projesine sağ tıklayın ve **Oluştur**' u seçin. Sınıf kitaplığı DLL dosyasının yeni bir sürümü derlenir ve derleme çıkış yoluna kaydedilir.

## <a name="run-the-updated-client-program"></a>Güncelleştirilmiş istemci programını çalıştır

Yapı çıkış klasörü konumuna gidin ve *TypeEquivalenceClient. exe*' yi çalıştırın. Konsol çıkışının artık, 2.0.0.0 derlemesinin yeni sürümünü, yeniden `TypeEquivalenceRuntime` Derlenmekte olan program *2.0.0.0*olmadan yansıttığını unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [-Link (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-bağlantı (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
- [C# programlama kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
