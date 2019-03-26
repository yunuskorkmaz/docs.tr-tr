---
title: .NET derlemeleri
ms.date: 07/10/2018
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
---
# <a name="assemblies-in-net"></a>.NET derlemeleri

Derlemeler dağıtım, sürüm denetimi, yeniden kullanma, aktivasyon kapsamı ve güvenlik izinleri için temel birimini oluşturur bir. AĞ tabanlı bir uygulama. Derlemeler, bir yürütülebilir (.exe) dosya veya dinamik bağlantı kitaplığı (.dll) dosyası biçiminde ve .NET uygulamalarının yapı taşlarıdır. Bunlar, ortak dil çalışma zamanı tür uygulamalarına dikkat etmeniz gereken bilgileri sağlar. Derleme türleri ve mantıksal bir işlevsellik birimi oluşturacak ve birlikte çalışmak üzere tasarlanan kaynakları koleksiyonu olarak düşünebilirsiniz.

.NET Core ve .NET Framework, bir derleme bir veya daha fazla kaynak kod dosyalarından oluşturulabilir. .NET Framework'teki derlemeler, bir veya daha fazla modül içerebilir. Bu, daha büyük projeleri birden fazla bireysel geliştiriciler ayrı kaynak kodu dosyaları veya tek bir derleme oluşturmak için birleştirilmiş modüller, iş şekilde planlanması sağlar. Modüller hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir çoklu dosya derlemesi oluşturmak](../../framework/app-domains/how-to-build-a-multifile-assembly.md).

Derlemeleri, aşağıdaki özelliklere sahiptir:

- Derlemeleri, .exe veya .dll dosyaları olarak uygulanır.

- .NET Framework'ü hedefleyen kitaplıklar için bir derleme koyarak uygulamalar arasında paylaşabilirsiniz [genel derleme önbelleği](../../framework/app-domains/gac.md). Derlemeleri güçlü-genel derleme önbelleğinde bulunan önce adlandırılması gerekir. Daha fazla bilgi için [Strong-Named derlemeleri](../../framework/app-domains/strong-named-assemblies.md).

- Derlemeleri, yalnızca gerekli olduğunda belleğe yüklenir. Kullanılmazlar, bunlar yüklü değildir. Başka bir deyişle, derlemeleri daha büyük projeler kaynakları yönetmek için etkili bir yol olabilir.

- Yansıma kullanarak program aracılığıyla bir derlemeyle ilgili bilgiler elde edebilirsiniz. Daha fazla bilgi için [yansıma (C#)](../../csharp/programming-guide/concepts/reflection.md) veya [yansıma (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Yalnızca bir yöntem çağırarak incelemek için bir derleme yüklediğiniz <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>.

## <a name="assembly-manifest"></a>Derleme bildirimi

Her derleme içinde bir *derleme bildirimi*. Benzer şekilde bir içindekiler tablosu, derleme bildirimi aşağıdakileri içerir:

- Derlemenin kimliğini (adı ve sürümü).

- Diğer tüm dosyaları tanımlayan bir dosya tablosu, diğer, .exe veya .dll dosyası, dayandığını oluşturulan derlemeleri veya hatta bit eşlem veya Benioku dosyası gibi bir derleme oluşturur.

- Bir *derleme başvurusu listesi*, tüm dış bağımlılıkları listesi verilmiştir: .dll veya diğer dosyaları uygulama gereksinimlerinizi başkası tarafından oluşturulmuş olabilir. Derleme başvuruları, genel ve özel nesnelere başvurular içerir. Genel nesneler, diğer tüm uygulamalar için kullanılabilir. ' De .NET Core, bunlar belirli bir .NET Core çalışma zamanı ile bağlı. .NET Framework'teki genel derleme önbelleğinde bulundukları. <xref:System.IO?displayProperty=nameWithType> Ad alanı genel derleme önbelleğindeki bir derleme bir örnektir. Özel nesneleri aynı düzeyde olarak veya uygulamanızı yüklendiği dizinin altında ya da bir dizin olmalıdır.

Derlemeleri içeriği, sürümleri ve bağımlılıkları hakkında bilgi içerdiğinden, bunları kullanan uygulamaları düzgün çalışması için Windows kayıt defteri değerlerine dayanan değil. Derlemeler .dll çakışmalarını azaltmak ve daha güvenilir ve kolay dağıtmak uygulamalarınızı. Çoğu durumda, yüklediğiniz bir. Hedef bilgisayarın dosyaları kopyalama powershell'inizi yazarak NET tabanlı uygulama. Daha fazla bilgi için [derleme bildirimi](../../framework/app-domains/assembly-manifest.md).

## <a name="adding-a-reference-to-an-assembly"></a>Bir derlemeye bir başvuru ekleme

Bir derlemeyi kullanması için buna bir başvuru eklemeniz gerekir. Ardından, kullanabileceğiniz [using yönergesi](../../csharp/language-reference/keywords/using-directive.md) için C# veya [Imports deyimi](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) Visual Basic'te'nın ad alanını kullanmak istediğiniz öğeleri seçin. Bir derlemeye başvuru ve içeri aktarıldıktan sonra erişilebilen tüm türler, özellikleri, yöntemleri ve diğer alt ad alanları üyeleri kodlarını kaynak dosyanıza bir parçası değilmiş gibi uygulamanızda kullanılabilir.

> [!NOTE]
> .NET sınıf kitaplığı çoğu derlemeleri otomatik olarak başvurulur. Bazı durumlarda, bir sistem derlemesi otomatik olarak başvurulabilir değil. ' De .NET Core, Visual Studio'da NuGet Paket Yöneticisi kullanılarak veya ekleyerek derlemeyi içeren NuGet paketine başvuru ekleyebilirsiniz. bir [ \<PackageReference >](../../core/tools/dependencies.md#the-new-packagereference-element) derlemesi için *.csproj öğesi veya *.vbproj projesi. .NET Framework derlemesine bir başvuru kullanarak ekleyebilirsiniz **Başvuru Ekle** iletişim kullanarak veya Visual Studio'da `-reference` için komut satırı seçeneği [ C# ](../../csharp/language-reference/compiler-options/reference-compiler-option.md) veya [ Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) derleyicileri.

C# ' ta aynı derlemenin iki sürümü de tek bir uygulama kullanabilirsiniz. Daha fazla bilgi için [extern diğer adı](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="creating-an-assembly"></a>Bir derleme oluşturma

Bunu Visual Studio'da, bunu komut satırından .NET Core komut satırı arabirimi (CLI) araçlarını kullanarak veya komut satırı derleyicisi ile .NET Framework derlemeleri oluştururken oluşturarak oluşturarak uygulamanızı derleyin. .NET CLI araçlarını kullanarak derlemeler oluşturma hakkında daha fazla bilgi için bkz. [.NET Core komut satırı arabirimi (CLI) araçlarını](../../core/tools/index.md). Komut satırı derleyicilerini sahip derlemeler oluşturmak için bkz: [csc.exe ile komut satırı derleme](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) için C# ve [komut satırından derleme](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) Visual Basic için.

> [!NOTE]
> Visual Studio'da bir derlemeyi derlemek için **derleme** menüsünde **yapı**.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET bütünleştirilmiş kodu dosya biçimi](file-format.md)
- [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Arkadaş Bütünleştirilmiş Kodları](friend-assemblies.md)
- [Nasıl yapılır: Yükleme ve yüklemelerini kaldırma derlemeleri (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Nasıl yapılır: Yük derlemeleri ve yüklemelerini kaldırma (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Nasıl yapılır: .NET Core’da Bütünleştirilmiş Kodu Kaldırabilme Özelliğini Kullanma ve Sorun Giderme](unloadability-howto.md)
- [Nasıl yapılır: Bir dosyanın derleme olup olmadığını belirleme (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
- [Nasıl yapılır: Bir dosyanın bir derleme (Visual Basic) olup olmadığını belirleme](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
