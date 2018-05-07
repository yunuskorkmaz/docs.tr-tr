---
title: "İzlenecek yol: Visual Studio'da (Visual Basic) yönetilen derlemelerden türler katıştırma"
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: 1f6176746b783d020c809fb0b5d55d741ce0148b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a>İzlenecek yol: Visual Studio'da (Visual Basic) yönetilen derlemelerden türler katıştırma
Tanımlayıcı adlı Yönetilen derleme tür bilgilerini katıştırma, geniş sürüm bağımsızlığı elde etmek için bir uygulamada türü eşleştiği. Diğer bir deyişle, her sürüm için derlenmesi gerek kalmadan yönetilen kitaplık birden fazla sürümünü türlerinden kullanmak için program yazılabilir.  
  
 Türü katıştırma Microsoft Office Otomasyon nesneleri kullanan bir uygulama gibi COM birlikte çalışma ile sık kullanılır. Tür bilgilerini katıştırma Microsoft Office'in farklı sürümlerinde farklı bilgisayarlarda çalışmak için bir programın aynı yapı sağlar. Ancak, tam olarak yönetilen bir çözüm katıştırma türü de kullanabilirsiniz.  
  
 Aşağıdaki özelliklere sahip bir derlemeden tür bilgileri katıştırılabilen:  
  
-   Derleme en az bir ortak arabirimi sunar.  
  
-   Katıştırılmış arabirimleri ile Açıklama eklenen bir `ComImport` özniteliğini ve bir `Guid` özniteliği (ve benzersiz bir GUID).  
  
-   Derleme ile Açıklama `ImportedFromTypeLib` özniteliği veya `PrimaryInteropAssembly` özniteliği ve derleme düzeyi `Guid` özniteliği. (Varsayılan olarak, Visual Basic proje şablonları derleme düzeyi dahil `Guid` özniteliği.)  
  
 Katıştırılabilen genel arabirimler belirttikten sonra bu arabirimleri uygulayan çalışma zamanı sınıfları oluşturabilirsiniz. Bir istemci programı daha sonra bu arabirimleri tasarım zamanında tür bilgileri ayarı ve ortak arabirimleri içeren derlemenin başvurarak eklenebilir `Embed Interop Types` referansı özelliğinin `True`. Bu komut satırı derleyicisini kullanarak ve kullanarak bütünleştirilmiş başvurma eşdeğerdir `/link` derleyici seçeneği. İstemci programı daha sonra bu arabirimleri olarak belirtilmiş, çalışma zamanı nesnelerinin örneklerini yükleyebilir. Tanımlayıcı adlı çalışma zamanı derlemesi yeni bir sürümünü oluşturursanız, istemci programı ile güncelleştirilmiş çalışma zamanı derlemesi derlenmesi gerekmez. Bunun yerine, istemcinin hangi sürümü çalışma zamanı derlemesi için ortak arabirimleri katıştırılmış tür bilgileri kullanarak, kullanılabilir kullanmaya devam eder.  
  
 COM birlikte çalışma derlemeleri türü bilgilerin destekliyoruz türü katıştırma birincil işlevi olduğu için tam olarak yönetilen bir çözümde tür bilgilerini katıştırma aşağıdaki sınırlamalar uygulanır:  
  
-   Yalnızca COM birlikte çalışma için belirli öznitelikleri katıştırılmış; diğer öznitelikleri göz ardı edilir.  
  
-   Genel parametreler bir türünü kullanır ve katıştırılmış türünün genel parametresi türü ise, bu tür bir derleme sınırından kullanılamaz. Başka bir derlemeye ait bir yöntemi çağırma bir derleme sınırını geçmesinden örnekleri dahil edin veya başka bir derlemede tanımlanan bir türü türetme bir türü.  
  
-   Sabitler katıştırılmış değil.  
  
-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Sınıf anahtarı olarak katıştırılmış bir türü desteklemiyor. Katıştırılmış bir tür bir anahtar olarak desteklemek için kendi Sözlük türü uygulayabilirsiniz.  
  
 Bu kılavuzda, aşağıdakileri:  
  
-   Katıştırılabilen tür bilgileri içeren ortak bir arabirim tanımlayıcı adlı bir derleme oluşturun.  
  
-   Ortak arabirimi uygulayan bir tanımlayıcı adlı çalışma zamanı derlemesi oluşturun.  
  
-   Ortak arabirimi tür bilgilerini katıştırır ve çalışma zamanı derlemesinden sınıfının bir örneği oluşturan bir istemci program oluşturun.  
  
-   Değiştirme ve çalışma zamanı derlemesi derleyin.  
  
-   Çalışma zamanı derlemesi yeni sürümünü istemci programı yeniden derlemenize gerek kalmadan kullanıldığını görmek için istemci programını çalıştırın.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a>Bir arabirim oluşturma  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a>Tür denkliği arabirimi projesi oluşturmak için  
  
1.  Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir. Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `TypeEquivalenceInterface`ve ardından **Tamam**. Yeni Proje oluşturulur.  
  
3.  İçinde **Çözüm Gezgini**, Class1.vb'ye dosyasını sağ tıklatın ve **yeniden adlandırma**. Dosyayı Yeniden Adlandır `ISampleInterface.vb` ve ENTER tuşuna basın. Dosyayı yeniden adlandırmak da yeniden adlandırın sınıfına `ISampleInterface`. Bu sınıf, sınıf için ortak arabirimi temsil eder.  
  
4.  TypeEquivalenceInterface projeyi sağ tıklatın ve **özellikleri**. Tıklatın **derleme** sekmesi. Çıkış yolu geliştirme bilgisayarınızda geçerli bir konuma ayarlı `C:\TypeEquivalenceSample`. Bu konum, bu kılavuzda bir sonraki adımda de kullanılır.  
  
5.  Hala proje özelliklerini düzenlerken tıklatın **imzalama** sekmesi. Seçin **derlemeyi imzalamak** seçeneği. İçinde **güçlü ad anahtar dosyası seçin** tıklatın **< yeni... >**. İçinde **anahtar dosya adını** kutusuna `key.snk`. Clear **my anahtar dosyasını bir parola ile koruyun** onay kutusu. **Tamam**'ı tıklatın.  
  
6.  ISampleInterface.vb dosyasını açın. ISampleInterface arabirimi oluşturmak üzere ISampleInterface sınıfı dosyasına aşağıdaki kodu ekleyin.  
  
    ```vb  
    Imports System.Runtime.InteropServices  
  
    <ComImport()>  
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>  
    Public Interface ISampleInterface  
        Sub GetUserInput()  
        ReadOnly Property UserInput As String  
    End Interface  
    ```  
  
7.  Üzerinde **Araçları** menüsünde tıklatın **Create GUID**. İçinde **Create GUID** iletişim kutusu, tıklatın **kayıt defteri biçimi** ve ardından **kopya**. **Çıkış**'a tıklayın.  
  
8.  İçinde `Guid` özniteliği, örnek GUID silme ve kopyalama GUID yapıştırın **Create GUID** iletişim kutusu. Küme ayraçları Kaldır ({}) kopyalanan Guid'den.  
  
9. Üzerinde **proje** menüsünde tıklatın **tüm dosyaları göster**.  
  
10. İçinde **Çözüm Gezgini**, genişletin **My proje** klasör. AssemblyInfo.vb çift tıklayın. Aşağıdaki öznitelik dosyasına ekleyin.  
  
    ```vb  
    <Assembly: ImportedFromTypeLib("")>  
    ```  
  
     Dosyayı kaydedin.  
  
11. Projeyi kaydedin.  
  
12. TypeEquivalenceInterface projeyi sağ tıklatın ve **yapı**. Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolu (örneğin, C:\TypeEquivalenceSample) kaydedilir.  
  
## <a name="creating-a-runtime-class"></a>Bir çalışma zamanı sınıf oluşturma  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a>Tür denkliği çalışma zamanı projesi oluşturmak için  
  
1.  Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir. Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `TypeEquivalenceRuntime`ve ardından **Tamam**. Yeni Proje oluşturulur.  
  
3.  İçinde **Çözüm Gezgini**, Class1.vb'ye dosyasını sağ tıklatın ve **yeniden adlandırma**. Dosyayı Yeniden Adlandır `SampleClass.vb` ve ENTER tuşuna basın. Dosyayı yeniden adlandırmak de yeniden adlandırır sınıfına `SampleClass`. Bu sınıf gerçekleştireceksiniz `ISampleInterface` arabirimi.  
  
4.  TypeEquivalenceRuntime projeyi sağ tıklatın ve **özellikleri**. Tıklatın **derleme** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolu ayarla `C:\TypeEquivalenceSample`.  
  
5.  Hala proje özelliklerini düzenlerken tıklatın **imzalama** sekmesi. Seçin **derlemeyi imzalamak** seçeneği. İçinde **güçlü ad anahtar dosyası seçin** tıklatın **< yeni... >**. İçinde **anahtar dosya adını** kutusuna `key.snk`. Clear **my anahtar dosyasını bir parola ile koruyun** onay kutusu. **Tamam**'ı tıklatın.  
  
6.  TypeEquivalenceRuntime projeyi sağ tıklatın ve **Başvuru Ekle**. Tıklatın **Gözat** sekmesinde ve çıkış yolu klasörüne göz atın. TypeEquivalenceInterface.dll dosyasını tıklatıp **Tamam**.  
  
7.  Üzerinde **proje** menüsünde tıklatın **tüm dosyaları göster**.  
  
8.  İçinde **Çözüm Gezgini**, genişletin **başvuruları** klasör. TypeEquivalenceInterface referans'ı seçin. TypeEquivalenceInterface başvuru Özellikler penceresinde ayarlayın **belirli bir sürüm** özelliğine **False**.  
  
9. SampleClass sınıfı oluşturmak için SampleClass sınıfı dosyasına aşağıdaki kodu ekleyin.  
  
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
  
11. TypeEquivalenceRuntime projeyi sağ tıklatın ve **yapı**. Sınıf kitaplığı .dll dosyası derlenmiş ve belirtilen yapı çıkış yolu (örneğin, C:\TypeEquivalenceSample) kaydedilir.  
  
## <a name="creating-a-client-project"></a>Bir istemci projesi oluşturma  
  
#### <a name="to-create-the-type-equivalence-client-project"></a>Tür denkliği istemci projesi oluşturmak için  
  
1.  Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir. Seçin **konsol uygulaması** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `TypeEquivalenceClient`ve ardından **Tamam**. Yeni Proje oluşturulur.  
  
3.  TypeEquivalenceClient projeyi sağ tıklatın ve **özellikleri**. Tıklatın **derleme** sekmesi. Örneğin, TypeEquivalenceInterface projesinde kullanılan aynı konuma çıkış yolu ayarla `C:\TypeEquivalenceSample`.  
  
4.  TypeEquivalenceClient projeyi sağ tıklatın ve **Başvuru Ekle**. Tıklatın **Gözat** sekmesinde ve çıkış yolu klasörüne göz atın. TypeEquivalenceInterface.dll dosyasını (TypeEquivalenceRuntime.dll değil) tıklatıp **Tamam**.  
  
5.  Üzerinde **proje** menüsünde tıklatın **tüm dosyaları göster**.  
  
6.  İçinde **Çözüm Gezgini**, genişletin **başvuruları** klasör. TypeEquivalenceInterface referans'ı seçin. TypeEquivalenceInterface başvuru Özellikler penceresinde ayarlayın **birlikte çalışma türlerini katıştır** özelliğine **doğru**.  
  
7.  İstemci programı oluşturmak için Module1.vb dosyasına aşağıdaki kodu ekleyin.  
  
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
  
8.  Derleme ve programı çalıştırmak için CTRL + F5 tuşuna basın.  
  
## <a name="modifying-the-interface"></a>Arabirim değiştirme  
  
#### <a name="to-modify-the-interface"></a>Arabirim değiştirmek için  
  
1.  Visual Studio'da üzerinde **dosya** menüsündeki **açık**ve ardından **proje/çözüm**.  
  
2.  İçinde **Proje Aç** iletişim kutusu, TypeEquivalenceInterface projesine sağ tıklayın ve ardından **özellikleri**. Tıklatın **uygulama** sekmesi. Tıklatın **derleme bilgilerini** düğmesi. Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.  
  
3.  ISampleInterface.vb dosyasını açın. Aşağıdaki kod satırını ISampleInterface arabirimi ekleyin.  
  
    ```vb  
    Function GetDate() As Date  
    ```  
  
     Dosyayı kaydedin.  
  
4.  Projeyi kaydedin.  
  
5.  TypeEquivalenceInterface projeyi sağ tıklatın ve **yapı**. Yeni bir sınıf kitaplığı .dll dosyasının sürümünü derlenmiş ve belirtilen yapı çıkış yolu (örneğin, C:\TypeEquivalenceSample) kaydedilir.  
  
## <a name="modifying-the-runtime-class"></a>Çalışma zamanı sınıfını değiştirme  
  
#### <a name="to-modify-the-runtime-class"></a>Çalışma zamanı sınıf değiştirmek için  
  
1.  Visual Studio'da üzerinde **dosya** menüsündeki **açık**ve ardından **proje/çözüm**.  
  
2.  İçinde **Proje Aç** iletişim kutusunda, TypeEquivalenceRuntime projeyi sağ tıklatın ve **özellikleri**. Tıklatın **uygulama** sekmesi. Tıklatın **derleme bilgilerini** düğmesi. Değişiklik **derleme sürümü** ve **dosya sürümü** değerler `2.0.0.0`.  
  
3.  SampleClass.vbfile açın. Aşağıdaki kod satırlarını SampleClass sınıfına ekleyin.  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  Projeyi kaydedin.  
  
5.  TypeEquivalenceRuntime projeyi sağ tıklatın ve **yapı**. Sınıf kitaplığı .dll dosyası güncelleştirilmiş bir sürümünü derlenmiş ve daha önce belirtilen yapı çıkış yolu (örneğin, C:\TypeEquivalenceSample) kaydedilir.  
  
6.  Dosya Gezgini'nde, çıkış yolunu klasörünü (örneğin, C:\TypeEquivalenceSample) açın. Programı çalıştırmak için TypeEquivalenceClient.exe çift tıklayın. Program, yeniden derlenmesi olmadan TypeEquivalenceRuntime derlemesinin yeni sürümü yansıtır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ Link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)  
 [Programlama Kavramları](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Bütünleştirilmiş Kodlarla Programlama](../../../../framework/app-domains/programming-with-assemblies.md)  
 [Derlemeler ve Genel Derleme Önbelleği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
