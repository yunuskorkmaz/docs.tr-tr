---
title: "İzlenecek yol: Visual Studio 'da yönetilen derlemelerden tür ekleme (C#)"
ms.date: 07/20/2015
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
ms.openlocfilehash: 5e6494f133128e3982aa07323d2c65b9fa5de47b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595799"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a>İzlenecek yol: Visual Studio 'da yönetilen derlemelerden tür ekleme (C#)

Tanımlayıcı adlı yönetilen bir derlemeden tür bilgilerini eklerseniz, sürüm bağımsızlığını elde etmek için bir uygulamada gevşek olarak birkaç tür oluşturabilirsiniz. Diğer bir deyişle, programınız her sürüm için yeniden derlenmesi gerekmeden yönetilen bir kitaplığın birden çok sürümündeki türleri kullanmak üzere yazılabilir.

Tür ekleme, genellikle Microsoft Office Otomasyon nesneleri kullanan bir uygulama gibi COM birlikte çalışma ile kullanılır. Tür bilgilerinin gömülmesi, farklı bilgisayarlarda farklı Microsoft Office sürümleriyle çalışmak için aynı programın derlemesini sağlar. Ancak, tam olarak yönetilen bir çözümle tür ekleme özelliğini de kullanabilirsiniz.

Tür bilgileri, aşağıdaki özelliklere sahip bir derlemeden gömülebilir:

- Derleme en az bir ortak arabirim kullanıma sunar.

- Katıştırılmış arabirimlere bir `ComImport` öznitelik ve bir `Guid` öznitelik (ve benzersiz bir GUID) eklenir.

- Derlemeye, `ImportedFromTypeLib` özniteliğiyle `PrimaryInteropAssembly` veya özniteliğiyle ve derleme düzeyi `Guid` özniteliğiyle açıklama eklenir. (Varsayılan olarak, görsel C# proje şablonları derleme düzeyi `Guid` bir öznitelik içerir.)

Katıştırılabilen ortak arabirimleri belirledikten sonra, bu arabirimleri uygulayan çalışma zamanı sınıfları oluşturabilirsiniz. Bir istemci program, ortak arabirimleri içeren derlemeye başvurarak ve `Embed Interop Types` `True`başvurusunun özelliğini ayarlayarak bu arabirimlerin tür bilgilerini tasarım zamanında ekleyebilir. Bu, komut satırı derleyicisini kullanma ve `/link` derleyici seçeneği kullanılarak derlemeye başvurma ile eşdeğerdir. İstemci programı daha sonra bu arabirimler olarak yazılmış çalışma zamanı nesnelerinizin örneklerini yükleyebilir. Güçlü adlandırılmış çalışma zamanı derlemenin yeni bir sürümünü oluşturursanız, istemci programın güncelleştirilmiş çalışma zamanı derlemesi ile yeniden derlenmesi gerekmez. Bunun yerine, istemci programı, ortak arabirimler için katıştırılmış tür bilgilerini kullanarak çalışma zamanı derlemesinin hangi sürümünün kullanılabilir olduğunu kullanmaya devam eder.

Ekleme türü birincil işlevi, COM birlikte çalışma derlemelerinden tür bilgilerinin gömülmesini destekletiğinden, tür bilgilerini tam olarak yönetilen bir çözüme eklediğinizde aşağıdaki sınırlamalar geçerlidir:

- Yalnızca COM birlikte çalışabilirliğine özgü öznitelikler katıştırılır; diğer öznitelikler yok sayılır.

- Bir tür genel parametreler kullanıyorsa ve genel parametrenin türü gömülü bir türse, bu tür bir derleme sınırı boyunca kullanılamaz. Bir derleme sınırının geçmesinin örnekleri, başka bir derlemeden bir yöntemi çağırmayı ya da başka bir derlemede tanımlanan türden bir tür türetmeyi içerir.

- Sabitler ekli değil.

- Sınıf <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> , gömülü bir türü anahtar olarak desteklemez. Gömülü bir türü anahtar olarak desteklemek için kendi sözlük türünü uygulayabilirsiniz.

Bu izlenecek yolda şunları yapacaksınız:

- Katıştırılabilen tür bilgilerini içeren bir ortak arabirime sahip güçlü adlı bir derleme oluşturun.

- Bu ortak arabirimi uygulayan, tanımlayıcı adlı bir çalışma zamanı derlemesi oluşturun.

- Ortak arabirimden tür bilgilerini katıştıran bir istemci programı oluşturun ve çalışma zamanı derlemesinden sınıfın bir örneğini oluşturur.

- Çalışma zamanı derlemesini değiştirin ve yeniden derleyin.

- İstemci programını yeniden derlemek zorunda kalmadan çalışma zamanı derlemesinin yeni sürümünün kullanıldığını görmek için istemci programını çalıştırın.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a>Arabirim oluşturma

#### <a name="to-create-the-type-equivalence-interface-project"></a>Tür denklik arabirimi projesi oluşturmak için

1. Visual Studio 'da, **Dosya** menüsünde **Yeni** ' yi seçin ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows** ' un seçili olduğundan emin olun. **Şablonlar** bölmesinde **sınıf kitaplığı** ' nı seçin. **Ad** kutusuna yazın `TypeEquivalenceInterface`ve ardından **Tamam**' a tıklayın. Yeni proje oluşturulur.

3. **Çözüm Gezgini**, Class1.cs dosyasına sağ tıklayın ve **Yeniden Adlandır**' a tıklayın. Dosyayı olarak `ISampleInterface.cs` yeniden adlandırın ve ENTER 'a basın. Dosyanın yeniden adlandırılması de sınıfı olarak `ISampleInterface`yeniden adlandırılacaktır. Bu sınıf, sınıfının genel arabirimini temsil eder.

4. TypeEquivalenceInterface projesine sağ tıklayın ve **Özellikler**' e tıklayın. **Derleme** sekmesine tıklayın. Çıkış yolunu, geliştirme bilgisayarınızda, `C:\TypeEquivalenceSample`gibi geçerli bir konuma ayarlayın. Bu konum, Bu izlenecek yolda daha sonraki bir adımda de kullanılacaktır.

5. Proje özelliklerini hala düzenleirken **imzalama** sekmesine tıklayın. **Derlemeyi imzala** seçeneğini belirleyin. **Tanımlayıcı ad seçin anahtar dosyası** listesinde  **\<yeni... öğesine tıklayın. >** . **Anahtar dosya adı** kutusuna yazın `key.snk`. **Anahtar dosyamı parolayla koru** onay kutusunu temizleyin. **Tamam**'ı tıklatın.

6. ISampleInterface.cs dosyasını açın. Iamptaınterface arabirimini oluşturmak için ısamptaınterface sınıf dosyasına aşağıdaki kodu ekleyin.

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

7. **Araçlar** menüsünde **GUID oluştur**' a tıklayın. **GUID oluştur** iletişim kutusunda, **kayıt defteri biçimi** ' ne ve ardından **Kopyala**' ya tıklayın. **Çıkış**'a tıklayın.

8. Özniteliğinde, örnek GUID 'yi silin ve **GUID oluştur** iletişim kutusundan kopyaladığınız GUID 'ye yapıştırın. `Guid` Kopyalanmış GUID 'den küme{}ayracı () kaldırın.

9. **Çözüm Gezgini**, **Özellikler** klasörünü genişletin. AssemblyInfo.cs dosyasına çift tıklayın. Dosyasına aşağıdaki özniteliği ekleyin.

    ```csharp
    [assembly: ImportedFromTypeLib("")]
    ```

     Dosyayı kaydedin.

10. Projeyi kaydedin.

11. TypeEquivalenceInterface projesine sağ tıklayın ve **Oluştur**' a tıklayın. Sınıf kitaplığı. dll dosyası derlenir ve belirtilen derleme çıkış yoluna (örneğin, C:\TypeEquivalenceSample) kaydedilir.

## <a name="creating-a-runtime-class"></a>Çalışma zamanı sınıfı oluşturma

#### <a name="to-create-the-type-equivalence-runtime-project"></a>Tür denklik çalışma zamanı projesi oluşturmak için

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.

2. **Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows** ' un seçili olduğundan emin olun. **Şablonlar** bölmesinde **sınıf kitaplığı** ' nı seçin. **Ad** kutusuna yazın `TypeEquivalenceRuntime`ve ardından **Tamam**' a tıklayın. Yeni proje oluşturulur.

3. **Çözüm Gezgini**, Class1.cs dosyasına sağ tıklayın ve **Yeniden Adlandır**' a tıklayın. Dosyayı olarak `SampleClass.cs` yeniden adlandırın ve ENTER 'a basın. Dosyanın yeniden adlandırılması de sınıfını olarak `SampleClass`yeniden adlandırır. Bu sınıf, `ISampleInterface` arabirimini uygular.

4. TypeEquivalenceRuntime projesine sağ tıklayın ve **Özellikler**' e tıklayın. **Derleme** sekmesine tıklayın. Çıkış yolunu, TypeEquivalenceInterface projesinde kullandığınız konuma ayarlayın, örneğin, `C:\TypeEquivalenceSample`.

5. Proje özelliklerini hala düzenleirken **imzalama** sekmesine tıklayın. **Derlemeyi imzala** seçeneğini belirleyin. **Tanımlayıcı ad seçin anahtar dosyası** listesinde  **\<yeni... öğesine tıklayın. >** . **Anahtar dosya adı** kutusuna yazın `key.snk`. **Anahtar dosyamı parolayla koru** onay kutusunu temizleyin. **Tamam**'ı tıklatın.

6. TypeEquivalenceRuntime projesine sağ tıklayın ve **Başvuru Ekle**' ye tıklayın. **Araştır** sekmesine tıklayın ve çıkış yolu klasörüne gidin. TypeEquivalenceInterface. dll dosyasını seçin ve **Tamam**' a tıklayın.

7. **Çözüm Gezgini**, **Başvurular** klasörünü genişletin. TypeEquivalenceInterface başvurusunu seçin. TypeEquivalenceInterface başvurusu için Özellikler penceresi, **belirli sürüm** özelliğini **false**olarak ayarlayın.

8. SampleClass sınıfını oluşturmak için SampleClass sınıf dosyasına aşağıdaki kodu ekleyin.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
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

9. Projeyi kaydedin.

10. TypeEquivalenceRuntime projesine sağ tıklayın ve **Oluştur**' a tıklayın. Sınıf kitaplığı. dll dosyası derlenir ve belirtilen derleme çıkış yoluna (örneğin, C:\TypeEquivalenceSample) kaydedilir.

## <a name="creating-a-client-project"></a>Istemci projesi oluşturma

#### <a name="to-create-the-type-equivalence-client-project"></a>Tür eşdeğerlik istemci projesi oluşturmak için

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.

2. **Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows** ' un seçili olduğundan emin olun. **Şablonlar** bölmesinde **konsol uygulaması** ' nı seçin. **Ad** kutusuna yazın `TypeEquivalenceClient`ve ardından **Tamam**' a tıklayın. Yeni proje oluşturulur.

3. TypeEquivalenceClient projesine sağ tıklayın ve **Özellikler**' e tıklayın. **Derleme** sekmesine tıklayın. Çıkış yolunu, TypeEquivalenceInterface projesinde kullandığınız konuma ayarlayın, örneğin, `C:\TypeEquivalenceSample`.

4. TypeEquivalenceClient projesine sağ tıklayın ve **Başvuru Ekle**' ye tıklayın. **Araştır** sekmesine tıklayın ve çıkış yolu klasörüne gidin. TypeEquivalenceInterface. dll dosyasını (TypeEquivalenceRuntime. dll değil) seçin ve **Tamam**' a tıklayın.

5. **Çözüm Gezgini**, **Başvurular** klasörünü genişletin. TypeEquivalenceInterface başvurusunu seçin. TypeEquivalenceInterface başvurusu için Özellikler penceresi, **birlikte çalışma türlerini katıştır** özelliğini **doğru**olarak ayarlayın.

6. İstemci programını oluşturmak için aşağıdaki kodu Program.cs dosyasına ekleyin.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using TypeEquivalenceInterface;
    using System.Reflection;

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

7. Programı derlemek ve çalıştırmak için CTRL + F5 tuşlarına basın.

## <a name="modifying-the-interface"></a>Arabirimi değiştirme

#### <a name="to-modify-the-interface"></a>Arabirimi değiştirmek için

1. Visual Studio 'da, **Dosya** menüsünde **Aç**' ın üzerine gelin ve ardından **Proje/çözüm**' e tıklayın.

2. **Proje Aç** Iletişim kutusunda TypeEquivalenceInterface projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın. **Uygulama** sekmesine tıklayın. **Derleme bilgileri** düğmesine tıklayın. **Derleme sürümünü** ve **dosya sürümü** değerlerini olarak `2.0.0.0`değiştirin.

3. SampleInterface.cs dosyasını açın. Aşağıdaki kod satırını ısamptaınterface arabirimine ekleyin.

    ```csharp
    DateTime GetDate();
    ```

    Dosyayı kaydedin.

4. Projeyi kaydedin.

5. TypeEquivalenceInterface projesine sağ tıklayın ve **Oluştur**' a tıklayın. Sınıf kitaplığı. dll dosyasının yeni bir sürümü, belirtilen derleme çıkış yolunda derlenir ve kaydedilir (örneğin, C:\TypeEquivalenceSample).

## <a name="modifying-the-runtime-class"></a>Çalışma zamanı sınıfını değiştirme

#### <a name="to-modify-the-runtime-class"></a>Çalışma zamanı sınıfını değiştirmek için

1. Visual Studio 'da, **Dosya** menüsünde **Aç**' ın üzerine gelin ve ardından **Proje/çözüm**' e tıklayın.

2. **Proje Aç** Iletişim kutusunda TypeEquivalenceRuntime projesine sağ tıklayın ve **Özellikler**' e tıklayın. **Uygulama** sekmesine tıklayın. **Derleme bilgileri** düğmesine tıklayın. **Derleme sürümünü** ve **dosya sürümü** değerlerini olarak `2.0.0.0`değiştirin.

3. SampleClass.cs dosyasını açın. Aşağıdaki kod satırlarını SampleClass sınıfına ekleyin.

    ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
    ```

    Dosyayı kaydedin.

4. Projeyi kaydedin.

5. TypeEquivalenceRuntime projesine sağ tıklayın ve **Oluştur**' a tıklayın. Sınıf kitaplığı. dll dosyasının güncelleştirilmiş bir sürümü, daha önce belirtilen derleme çıkış yolunda derlenir ve kaydedilir (örneğin, C:\TypeEquivalenceSample).

6. Dosya Gezgini 'nde çıkış yolu klasörünü açın (örneğin, C:\TypeEquivalenceSample). Programı çalıştırmak için TypeEquivalenceClient. exe dosyasına çift tıklayın. Program, TypeEquivalenceRuntime derlemesinin yeni sürümünü yeniden derlenmeden yansıtır.

## <a name="see-also"></a>Ayrıca bkz.

- [/Link (C# derleyici seçenekleri)](../../../language-reference/compiler-options/link-compiler-option.md)
- [C# Programlama Kılavuzu](../../index.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../../../framework/app-domains/programming-with-assemblies.md)
- [.NET’te bütünleştirilmiş kodlar](../../../../standard/assembly/index.md)
