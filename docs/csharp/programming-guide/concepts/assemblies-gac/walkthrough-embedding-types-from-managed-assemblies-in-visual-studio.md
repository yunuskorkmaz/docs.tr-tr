---
title: "İzlenecek yol: Visual Studio'da (C#) yönetilen derlemelerden türler katıştırma"
ms.date: 07/20/2015
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
ms.openlocfilehash: 1900c62d1ebaf611f141f8f1bdf95f8d11f82140
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201263"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a>İzlenecek yol: Visual Studio'da (C#) yönetilen derlemelerden türler katıştırma
Tanımlayıcı adlı bir yönetilen bütünleştirilmiş koddan tür bilgilerini katıştırma, sürüm bağımsızlığı elde etmek için bir uygulama türlerinde gevşek mümkündür. Diğer bir deyişle, programınız her sürüm için derlenmesi zorunda kalmadan bir yönetilen kitaplık birden çok sürümünden türler kullanmak üzere yazılabilir.  
  
 Ekleme türü Microsoft Office'ten Otomasyon nesneleri kullanan bir uygulama gibi COM birlikte çalışma ile sık kullanılır. Tür bilgilerini katıştırma farklı bilgisayarlarda Microsoft Office'in farklı sürümlerinde çalışmak için bir programın aynı yapısının sağlar. Ancak, tam olarak yönetilen bir Çözümle ekleme türü de kullanabilirsiniz.  
  
 Tür bilgileri aşağıdaki özelliklere sahip bir derlemeden eklenebilir:  
  
-   Derleme en az bir ortak arabirim kullanıma sunar.  
  
-   Katıştırılmış arabirimleri ile açıklamalı olan bir `ComImport` özniteliği ve `Guid` özniteliği (ve benzersiz bir GUID).  
  
-   Derleme ile açıklanıyor `ImportedFromTypeLib` özniteliği veya `PrimaryInteropAssembly` özniteliğini ve bir derleme düzeyi `Guid` özniteliği. (Varsayılan olarak, Visual C# proje şablonlarında derleme düzeyi dahil `Guid` özniteliği.)  
  
 Eklenebilecek Ortak arabirimlerin belirttikten sonra bu arabirimleri uygulayan çalışma zamanı sınıflar oluşturabilirsiniz. Bir istemci programını sonra bu arabirimleri için tasarım zamanında tür bilgilerini genel arabirimleri ve ayar içeren derleme başvurarak katıştırabilirsiniz `Embed Interop Types` özelliği için başvuru `True`. Bu komut satırı derleyicisini kullanarak ve kullanarak derlemenin başvurduğu eşdeğerdir `/link` derleyici seçeneği. İstemci programı daha sonra bu arabirimleri olarak yazılan, çalışma zamanı nesnelerinin örneklerini yükleyebilirsiniz. Çalışma zamanı tanımlayıcı adlı bütünleştirilmiş kodunuzda yeni bir sürümü oluşturursanız, güncelleştirilmiş çalışma zamanı derleme ile derlenmesi istemci program yok. Bunun yerine, istemci programı, ortak arabirimler için gömülü tür bilgileri kullanarak hangi çalışma zamanı derleme sürümü, kullanıma hazır kullanmaya devam eder.  
  
 Tür bilgilerini COM birlikte çalışma derlemelerini, destekliyoruz türü ekleme birincil işlevi olduğu için tam olarak yönetilen bir çözümde tür bilgilerini katıştırma aşağıdaki sınırlamalar geçerlidir:  
  
-   Yalnızca COM birlikte çalışma için belirli öznitelikleri katıştırılmış; diğer öznitelikler yok sayılır.  
  
-   Bir tür genel parametreleri kullanan ve katıştırılmış tür genel parametre türü ise, bu tür bir bütünleştirilmiş kod sınırları arasında kullanılamaz. Başka bir derlemeden bir yöntemi çağırmak bir derleme sınırı aşan örnekleri şunlardır veya başka bir derlemede tanımlanan bir türü türetilen bir tür.  
  
-   Sabitler ekli değil.  
  
-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Sınıfı, bir anahtar olarak gömülü bir türünü desteklemiyor. Katıştırılmış tür olarak bir anahtar desteklemek için kendi Sözlük türü uygulayabilirsiniz.  
  
 Bu kılavuzda, aşağıdakileri yapmanız:  
  
-   Eklenebilecek tür bilgilerini içeren bir ortak arabirim kesin adlandırılmış bir derleme oluşturun.  
  
-   Genel arabirimi uygulayan bir çalışma zamanı tanımlayıcı adlı bütünleştirilmiş kod oluşturun.  
  
-   Ortak arabirim tür bilgilerini katıştırır ve çalışma zamanı derlemenin sınıfının bir örneğini oluşturan bir istemci programı oluşturun.  
  
-   Değiştirin ve çalışma zamanı derleme yeniden derleyin.  
  
-   İstemcinin yeniden derlemenize gerek kalmadan yeni çalışma zamanı derleme sürümünü kullanılmakta olduğunu görmek için istemci programı çalıştırın.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a>Bir arabirim oluşturma  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a>Tür eşdeğerliği arabirimi projesi oluşturmak için  
  
1.  Visual Studio'da üzerinde **dosya** menüsünde seçin **yeni** ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir. Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `TypeEquivalenceInterface`ve ardından **Tamam**. Yeni Proje oluşturulur.  
  
3.  İçinde **Çözüm Gezgini**, Class1.cs dosyasını sağ tıklatıp **Yeniden Adlandır**. Dosyayı Yeniden Adlandır `ISampleInterface.cs` ve ENTER tuşuna basın. Dosya yeniden adlandırılırken da yeniden adlandırmak sınıfa `ISampleInterface`. Bu sınıf, sınıf için ortak arabirimi temsil eder.  
  
4.  TypeEquivalenceInterface projeyi sağ tıklatıp **özellikleri**. Tıklayın **derleme** sekmesi. Çıkış yolu geçerli bir konum, geliştirme bilgisayarınızda gibi ayarlamak `C:\TypeEquivalenceSample`. Bu konum, ayrıca bu izlenecek yolda bir sonraki adımda kullanılır.  
  
5.  Yine de proje özelliklerini düzenlerken tıklayın **imzalama** sekmesi. Seçin **derlemeyi imzalamayı** seçeneği. İçinde **bir tanımlayıcı ad anahtar dosyası seç** listesinde **< Yeni … >**. İçinde **anahtar dosya adı** kutusuna `key.snk`. NET **anahtar dosyamı bir parolayla korumak** onay kutusu. **Tamam**'ı tıklatın.  
  
6.  ISampleInterface.cs dosyasını açın. Aşağıdaki kodu ISampleInterface arabirimi oluşturmak için ISampleInterface sınıf dosyası ekleyin.  
  
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
  
7.  Üzerinde **Araçları** menüsünü tıklatın **GUID Oluştur**. İçinde **GUID Oluştur** iletişim kutusu, tıklayın **biçimi kayıt defteri** ve ardından **kopyalama**. **Çıkış**'a tıklayın.  
  
8.  İçinde `Guid` özniteliği, örnek GUID silin ve kopyalama GUID yapıştırın **GUID Oluştur** iletişim kutusu. Küme ayraçları Kaldır ({}) kopyalanan Guid'den.  
  
9. İçinde **Çözüm Gezgini**, genişletme **özellikleri** klasör. AssemblyInfo.cs dosyasını çift tıklayın. Dosyaya şu özniteliği ekleyin.  
  
    ```csharp  
    [assembly: ImportedFromTypeLib("")]  
    ```  
  
     Dosyayı kaydedin.  
  
10. Projeyi kaydedin.  
  
11. TypeEquivalenceInterface projeyi sağ tıklatıp **yapı**. Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolunu (örneğin, C:\TypeEquivalenceSample) kaydedildi.  
  
## <a name="creating-a-runtime-class"></a>Bir çalışma zamanı sınıf oluşturma  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a>Tür eşdeğerliği çalışma zamanı projesi oluşturmak için  
  
1.  Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir. Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `TypeEquivalenceRuntime`ve ardından **Tamam**. Yeni Proje oluşturulur.  
  
3.  İçinde **Çözüm Gezgini**, Class1.cs dosyasını sağ tıklatıp **Yeniden Adlandır**. Dosyayı Yeniden Adlandır `SampleClass.cs` ve ENTER tuşuna basın. Dosya yeniden adlandırılırken da yeniden adlandırır sınıfa `SampleClass`. Bu sınıf uygulayacak `ISampleInterface` arabirimi.  
  
4.  TypeEquivalenceRuntime projeyi sağ tıklatıp **özellikleri**. Tıklayın **derleme** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolunu ayarlayın `C:\TypeEquivalenceSample`.  
  
5.  Yine de proje özelliklerini düzenlerken tıklayın **imzalama** sekmesi. Seçin **derlemeyi imzalamayı** seçeneği. İçinde **bir tanımlayıcı ad anahtar dosyası seç** listesinde **< Yeni … >**. İçinde **anahtar dosya adı** kutusuna `key.snk`. NET **anahtar dosyamı bir parolayla korumak** onay kutusu. **Tamam**'ı tıklatın.  
  
6.  TypeEquivalenceRuntime projeyi sağ tıklatıp **Başvuru Ekle**. Tıklayın **Gözat** sekmesini ve çıkış yol klasöre göz atın. TypeEquivalenceInterface.dll dosyasını seçin ve tıklayın **Tamam**.  
  
7.  İçinde **Çözüm Gezgini**, genişletme **başvuruları** klasör. TypeEquivalenceInterface başvurusunu seçin. TypeEquivalenceInterface başvurusu için Özellikler penceresinde ayarlayın **belirli sürüm** özelliğini **False**.  
  
8.  Aşağıdaki kodu SampleClass sınıfı oluşturmak için SampleClass sınıf dosyası ekleyin.  
  
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
    )  
    ```  
  
9. Projeyi kaydedin.  
  
10. TypeEquivalenceRuntime projeyi sağ tıklatıp **yapı**. Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolunu (örneğin, C:\TypeEquivalenceSample) kaydedildi.  
  
## <a name="creating-a-client-project"></a>Bir istemci projesi oluşturma  
  
#### <a name="to-create-the-type-equivalence-client-project"></a>Tür eşdeğerliği istemci projesi oluşturmak için  
  
1.  Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir. Seçin **konsol uygulaması** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `TypeEquivalenceClient`ve ardından **Tamam**. Yeni Proje oluşturulur.  
  
3.  TypeEquivalenceClient projeyi sağ tıklatıp **özellikleri**. Tıklayın **derleme** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolunu ayarlayın `C:\TypeEquivalenceSample`.  
  
4.  TypeEquivalenceClient projeyi sağ tıklatıp **Başvuru Ekle**. Tıklayın **Gözat** sekmesini ve çıkış yol klasöre göz atın. TypeEquivalenceInterface.dll dosyası (TypeEquivalenceRuntime.dll değil) seçin ve tıklayın **Tamam**.  
  
5.  İçinde **Çözüm Gezgini**, genişletme **başvuruları** klasör. TypeEquivalenceInterface başvurusunu seçin. TypeEquivalenceInterface başvurusu için Özellikler penceresinde ayarlayın **birlikte çalışma türlerini katıştır** özelliğini **True**.  
  
6.  İstemci programı oluşturmak için Program.cs dosyasına aşağıdaki kodu ekleyin.  
  
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
  
7.  Derleme ve programı çalıştırmak için CTRL + F5 tuşlarına basın.  
  
## <a name="modifying-the-interface"></a>Arabirim değiştirme  
  
#### <a name="to-modify-the-interface"></a>Arabirim değiştirmek için  
  
1.  Visual Studio'da üzerinde **dosya** menüsünde **açık**ve ardından **proje/çözüm**.  
  
2.  İçinde **Proje Aç** iletişim kutusu, TypeEquivalenceInterface projeye sağ tıklayın ve ardından **özellikleri**. Tıklayın **uygulama** sekmesi. Tıklayın **derleme bilgilerini** düğmesi. Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.  
  
3.  SampleInterface.cs dosyasını açın. Aşağıdaki kod satırını ISampleInterface arabirimi ekleyin.  
  
    ```csharp  
    DateTime GetDate();  
    ```  
  
     Dosyayı kaydedin.  
  
4.  Projeyi kaydedin.  
  
5.  TypeEquivalenceInterface projeyi sağ tıklatıp **yapı**. Sınıf kitaplığı .dll dosyasını yeni bir sürümü derlenmiş ve belirtilen yapı çıkış yoluna (örneğin, C:\TypeEquivalenceSample) kaydedilir.  
  
## <a name="modifying-the-runtime-class"></a>Çalışma zamanı sınıf değiştirme  
  
#### <a name="to-modify-the-runtime-class"></a>Çalışma zamanı sınıf değiştirmek için  
  
1.  Visual Studio'da üzerinde **dosya** menüsünde **açık**ve ardından **proje/çözüm**.  
  
2.  İçinde **Proje Aç** iletişim kutusuna TypeEquivalenceRuntime projeye sağ tıklayın ve tıklatın **özellikleri**. Tıklayın **uygulama** sekmesi. Tıklayın **derleme bilgilerini** düğmesi. Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.  
  
3.  SampleClass.cs dosyasını açın. Aşağıdaki kod satırlarını SampleClass sınıfına ekleyin.  
  
    ```csharp  
    public DateTime GetDate()  
    {  
        return DateTime.Now;  
    }  
    ```  
  
     Dosyayı kaydedin.  
  
4.  Projeyi kaydedin.  
  
5.  TypeEquivalenceRuntime projeyi sağ tıklatıp **yapı**. Sınıf kitaplığı .dll dosyası güncelleştirilmiş bir sürümünü derlenmiş ve daha önce belirtilen yapı çıkış yoluna (örneğin, C:\TypeEquivalenceSample) kaydedilir.  
  
6.  Dosya Gezgini'nde, çıkış yolu klasörü (örneğin, C:\TypeEquivalenceSample) açın. Programı çalıştırmak üzere TypeEquivalenceClient.exe çift tıklayın. Program, yeniden derlenen kalmadan TypeEquivalenceRuntime derlemenin yeni sürümü yansıtır.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [/ Link (C# Derleyici Seçenekleri)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)  
- [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)  
- [Bütünleştirilmiş Kodlarla Programlama](../../../../framework/app-domains/programming-with-assemblies.md)  
- [Derlemeler ve Genel Derleme Önbelleği (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
