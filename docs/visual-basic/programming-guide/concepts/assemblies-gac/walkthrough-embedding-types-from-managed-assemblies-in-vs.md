---
title: "İzlenecek yol: Visual Studio'da (Visual Basic) yönetilen derlemelerden türler katıştırma"
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: 0c0de529a0005c9dbaf1f8d0f25957b217280e31
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753014"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a>İzlenecek yol: Visual Studio'da (Visual Basic) yönetilen derlemelerden türler katıştırma

Tanımlayıcı adlı bir yönetilen bütünleştirilmiş koddan tür bilgilerini katıştırma, sürüm bağımsızlığı elde etmek için bir uygulama türlerinde gevşek mümkündür. Diğer bir deyişle, programınız her sürüm için derlenmesi zorunda kalmadan bir yönetilen kitaplık birden çok sürümünden türler kullanmak üzere yazılabilir.

Ekleme türü Microsoft Office'ten Otomasyon nesneleri kullanan bir uygulama gibi COM birlikte çalışma ile sık kullanılır. Tür bilgilerini katıştırma farklı bilgisayarlarda Microsoft Office'in farklı sürümlerinde çalışmak için bir programın aynı yapısının sağlar. Ancak, tam olarak yönetilen bir Çözümle ekleme türü de kullanabilirsiniz.

Tür bilgileri aşağıdaki özelliklere sahip bir derlemeden eklenebilir:

- Derleme en az bir ortak arabirim kullanıma sunar.

- Katıştırılmış arabirimleri ile açıklamalı olan bir `ComImport` özniteliği ve `Guid` özniteliği (ve benzersiz bir GUID).

- Derleme ile açıklanıyor `ImportedFromTypeLib` özniteliği veya `PrimaryInteropAssembly` özniteliğini ve bir derleme düzeyi `Guid` özniteliği. (Varsayılan olarak, Visual Basic proje şablonları, bir derleme düzeyi dahil `Guid` özniteliği.)

Eklenebilecek Ortak arabirimlerin belirttikten sonra bu arabirimleri uygulayan çalışma zamanı sınıflar oluşturabilirsiniz. Bir istemci programını sonra bu arabirimleri için tasarım zamanında tür bilgilerini genel arabirimleri ve ayar içeren derleme başvurarak katıştırabilirsiniz `Embed Interop Types` özelliği için başvuru `True`. Bu komut satırı derleyicisini kullanarak ve kullanarak derlemenin başvurduğu eşdeğerdir `/link` derleyici seçeneği. İstemci programı daha sonra bu arabirimleri olarak yazılan, çalışma zamanı nesnelerinin örneklerini yükleyebilirsiniz. Çalışma zamanı tanımlayıcı adlı bütünleştirilmiş kodunuzda yeni bir sürümü oluşturursanız, güncelleştirilmiş çalışma zamanı derleme ile derlenmesi istemci program yok. Bunun yerine, istemci programı, ortak arabirimler için gömülü tür bilgileri kullanarak hangi çalışma zamanı derleme sürümü, kullanıma hazır kullanmaya devam eder.

Tür bilgilerini COM birlikte çalışma derlemelerini, destekliyoruz türü ekleme birincil işlevi olduğu için tam olarak yönetilen bir çözümde tür bilgilerini katıştırma aşağıdaki sınırlamalar geçerlidir:

- Yalnızca COM birlikte çalışma için belirli öznitelikleri katıştırılmış; diğer öznitelikler yok sayılır.

- Bir tür genel parametreleri kullanan ve katıştırılmış tür genel parametre türü ise, bu tür bir bütünleştirilmiş kod sınırları arasında kullanılamaz. Başka bir derlemeden bir yöntemi çağırmak bir derleme sınırı aşan örnekleri şunlardır veya başka bir derlemede tanımlanan bir türü türetilen bir tür.

- Sabitler ekli değil.

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Sınıfı, bir anahtar olarak gömülü bir türünü desteklemiyor. Katıştırılmış tür olarak bir anahtar desteklemek için kendi Sözlük türü uygulayabilirsiniz.

 Bu kılavuzda, aşağıdakileri yapmanız:

- Eklenebilecek tür bilgilerini içeren bir ortak arabirim kesin adlandırılmış bir derleme oluşturun.

- Genel arabirimi uygulayan bir çalışma zamanı tanımlayıcı adlı bütünleştirilmiş kod oluşturun.

- Ortak arabirim tür bilgilerini katıştırır ve çalışma zamanı derlemenin sınıfının bir örneğini oluşturan bir istemci programı oluşturun.

- Değiştirin ve çalışma zamanı derleme yeniden derleyin.

- İstemcinin yeniden derlemenize gerek kalmadan yeni çalışma zamanı derleme sürümünü kullanılmakta olduğunu görmek için istemci programı çalıştırın.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a>Bir arabirim oluşturma

### <a name="to-create-the-type-equivalence-interface-project"></a>Tür eşdeğerliği arabirimi projesi oluşturmak için

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.

2. İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir. Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `TypeEquivalenceInterface`ve ardından **Tamam**. Yeni Proje oluşturulur.

3. İçinde **Çözüm Gezgini**Class1.vb dosyaya sağ tıklayın ve tıklayın **Yeniden Adlandır**. Dosyayı Yeniden Adlandır `ISampleInterface.vb` ve ENTER tuşuna basın. Dosya yeniden adlandırılırken da yeniden adlandırmak sınıfa `ISampleInterface`. Bu sınıf, sınıf için ortak arabirimi temsil eder.

4. TypeEquivalenceInterface projeyi sağ tıklatıp **özellikleri**. Tıklayın **derleme** sekmesi. Çıkış yolu geçerli bir konum, geliştirme bilgisayarınızda gibi ayarlamak `C:\TypeEquivalenceSample`. Bu konum, ayrıca bu izlenecek yolda bir sonraki adımda kullanılır.

5. Yine de proje özelliklerini düzenlerken tıklayın **imzalama** sekmesi. Seçin **derlemeyi imzalamayı** seçeneği. İçinde **bir tanımlayıcı ad anahtar dosyası seç** listesinde **< Yeni … >** . İçinde **anahtar dosya adı** kutusuna `key.snk`. NET **anahtar dosyamı bir parolayla korumak** onay kutusu. **Tamam**'ı tıklatın.

6. ISampleInterface.vb dosyasını açın. Aşağıdaki kodu ISampleInterface arabirimi oluşturmak için ISampleInterface sınıf dosyası ekleyin.

    ```vb
    Imports System.Runtime.InteropServices

    <ComImport()>
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
    Public Interface ISampleInterface
        Sub GetUserInput()
        ReadOnly Property UserInput As String
    End Interface
    ```

7. Üzerinde **Araçları** menüsünü tıklatın **GUID Oluştur**. İçinde **GUID Oluştur** iletişim kutusu, tıklayın **biçimi kayıt defteri** ve ardından **kopyalama**. **Çıkış**'a tıklayın.

8. İçinde `Guid` özniteliği, örnek GUID silin ve kopyalama GUID yapıştırın **GUID Oluştur** iletişim kutusu. Küme ayraçları Kaldır ({}) kopyalanan Guid'den.

9. Üzerinde **proje** menüsünü tıklatın **tüm dosyaları göster**.

10. İçinde **Çözüm Gezgini**, genişletme **Projem** klasör. AssemblyInfo.vb çift tıklayın. Dosyaya şu özniteliği ekleyin.

    ```vb
    <Assembly: ImportedFromTypeLib("")>
    ```

    Dosyayı kaydedin.

11. Projeyi kaydedin.

12. TypeEquivalenceInterface projeyi sağ tıklatıp **yapı**. Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolunu (örneğin, C:\TypeEquivalenceSample) kaydedildi.

## <a name="creating-a-runtime-class"></a>Bir çalışma zamanı sınıf oluşturma

### <a name="to-create-the-type-equivalence-runtime-project"></a>Tür eşdeğerliği çalışma zamanı projesi oluşturmak için

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.

2. İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir. Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `TypeEquivalenceRuntime`ve ardından **Tamam**. Yeni Proje oluşturulur.

3. İçinde **Çözüm Gezgini**Class1.vb dosyaya sağ tıklayın ve tıklayın **Yeniden Adlandır**. Dosyayı Yeniden Adlandır `SampleClass.vb` ve ENTER tuşuna basın. Dosya yeniden adlandırılırken da yeniden adlandırır sınıfa `SampleClass`. Bu sınıf uygulayacak `ISampleInterface` arabirimi.

4. TypeEquivalenceRuntime projeyi sağ tıklatıp **özellikleri**. Tıklayın **derleme** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolunu ayarlayın `C:\TypeEquivalenceSample`.

5. Yine de proje özelliklerini düzenlerken tıklayın **imzalama** sekmesi. Seçin **derlemeyi imzalamayı** seçeneği. İçinde **bir tanımlayıcı ad anahtar dosyası seç** listesinde **< Yeni … >** . İçinde **anahtar dosya adı** kutusuna `key.snk`. NET **anahtar dosyamı bir parolayla korumak** onay kutusu.           **Tamam**'ı tıklatın.

6. TypeEquivalenceRuntime projeyi sağ tıklatıp **Başvuru Ekle**. Tıklayın **Gözat** sekmesini ve çıkış yol klasöre göz atın. TypeEquivalenceInterface.dll dosyasını seçin ve tıklayın **Tamam**.

7. Üzerinde **proje** menüsünü tıklatın **tüm dosyaları göster**.

8. İçinde **Çözüm Gezgini**, genişletme **başvuruları** klasör. TypeEquivalenceInterface başvurusunu seçin. TypeEquivalenceInterface başvurusu için Özellikler penceresinde ayarlayın **belirli sürüm** özelliğini **False**.

9. Aşağıdaki kodu SampleClass sınıfı oluşturmak için SampleClass sınıf dosyası ekleyin.

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

10. Projeyi kaydedin.

11. TypeEquivalenceRuntime projeyi sağ tıklatıp **yapı**. Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolunu (örneğin, C:\TypeEquivalenceSample) kaydedildi.

## <a name="creating-a-client-project"></a>Bir istemci projesi oluşturma

### <a name="to-create-the-type-equivalence-client-project"></a>Tür eşdeğerliği istemci projesi oluşturmak için

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.

2. İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir. Seçin **konsol uygulaması** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `TypeEquivalenceClient`ve ardından **Tamam**. Yeni Proje oluşturulur.

3. TypeEquivalenceClient projeyi sağ tıklatıp **özellikleri**. Tıklayın **derleme** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolunu ayarlayın `C:\TypeEquivalenceSample`.

4. TypeEquivalenceClient projeyi sağ tıklatıp **Başvuru Ekle**. Tıklayın **Gözat** sekmesini ve çıkış yol klasöre göz atın. TypeEquivalenceInterface.dll dosyası (TypeEquivalenceRuntime.dll değil) seçin ve tıklayın **Tamam**.

5. Üzerinde **proje** menüsünü tıklatın **tüm dosyaları göster**.

6. İçinde **Çözüm Gezgini**, genişletme **başvuruları** klasör. TypeEquivalenceInterface başvurusunu seçin. TypeEquivalenceInterface başvurusu için Özellikler penceresinde ayarlayın **birlikte çalışma türlerini katıştır** özelliğini **True**.

7. İstemci programı oluşturma işleminin Module1.vb dosyaya aşağıdaki kodu ekleyin.

    ```vb
    Imports TypeEquivalenceInterface
    Imports System.Reflection

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

8. Derleme ve programı çalıştırmak için CTRL + F5 tuşlarına basın.

## <a name="modifying-the-interface"></a>Arabirim değiştirme

### <a name="to-modify-the-interface"></a>Arabirim değiştirmek için

1. Visual Studio'da üzerinde **dosya** menüsünde **açık**ve ardından **proje/çözüm**.

2. İçinde **Proje Aç** iletişim kutusu, TypeEquivalenceInterface projeye sağ tıklayın ve ardından **özellikleri**. Tıklayın **uygulama** sekmesi. Tıklayın **derleme bilgilerini** düğmesi. Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.

3. ISampleInterface.vb dosyasını açın. Aşağıdaki kod satırını ISampleInterface arabirimi ekleyin.

    ```vb
    Function GetDate() As Date
    ```

    Dosyayı kaydedin.

4. Projeyi kaydedin.

5. TypeEquivalenceInterface projeyi sağ tıklatıp **yapı**. Sınıf kitaplığı .dll dosyasını yeni bir sürümü derlenmiş ve belirtilen yapı çıkış yoluna (örneğin, C:\TypeEquivalenceSample) kaydedilir.

## <a name="modifying-the-runtime-class"></a>Çalışma zamanı sınıf değiştirme

### <a name="to-modify-the-runtime-class"></a>Çalışma zamanı sınıf değiştirmek için

1. Visual Studio'da üzerinde **dosya** menüsünde **açık**ve ardından **proje/çözüm**.

2. İçinde **Proje Aç** iletişim kutusuna TypeEquivalenceRuntime projeye sağ tıklayın ve tıklatın **özellikleri**. Tıklayın **uygulama** sekmesi. Tıklayın **derleme bilgilerini** düğmesi. Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.

3. SampleClass.vb dosyasını açın. Aşağıdaki kod satırlarını SampleClass sınıfına ekleyin.

    ```vb
    Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
        Return Now
    End Function
    ```

    Dosyayı kaydedin.

4. Projeyi kaydedin.

5. TypeEquivalenceRuntime projeyi sağ tıklatıp **yapı**. Sınıf kitaplığı .dll dosyası güncelleştirilmiş bir sürümünü derlenmiş ve daha önce belirtilen yapı çıkış yoluna (örneğin, C:\TypeEquivalenceSample) kaydedilir.

6. Dosya Gezgini'nde, çıkış yolu klasörü (örneğin, C:\TypeEquivalenceSample) açın. Programı çalıştırmak üzere TypeEquivalenceClient.exe çift tıklayın. Program, yeniden derlenen kalmadan TypeEquivalenceRuntime derlemenin yeni sürümü yansıtır.

## <a name="see-also"></a>Ayrıca bkz.

- [/ Link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)
- [Programlama Kavramları](../../../../visual-basic/programming-guide/concepts/index.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../../../framework/app-domains/programming-with-assemblies.md)
- [.NET’te bütünleştirilmiş kodlar](../../../../standard/assembly/index.md)
