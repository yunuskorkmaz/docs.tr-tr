---
title: 'Nasıl yapılır: COM Sarmalayıcıları Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 035d6439ec90426d7b68e05043ea8b6722f81d28
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121595"
---
# <a name="how-to-create-com-wrappers"></a>Nasıl yapılır: COM Sarmalayıcıları Oluşturma

Visual Studio 2005 özelliklerini veya .NET Framework araçlarını kullanarak Component Object Model (COM) sarmalayıcıları oluşturabilirsiniz. Her iki yöntem de iki tür COM sarmalayıcı oluşturur:

- Yönetilen kodda com nesnesini çalıştırmak için bir tür kitaplığından [Runtime Çağrılabilir Sarılayıcı.](../../standard/native-interop/runtime-callable-wrapper.md)

- Yerel bir uygulamada yönetilen bir nesneyi çalıştırmak için gerekli kayıt defteri ayarlarına sahip [com çağrılabilir sarıcı.](../../standard/native-interop/com-callable-wrapper.md)

Visual Studio 2005'te, PROJENIZE referans olarak COM sarıcıyı ekleyebilirsiniz.

## <a name="wrap-com-objects-in-a-managed-application"></a>Yönetilen Bir Uygulamada COM Nesnelerini Kaydırma

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Visual Studio'u kullanarak çalışma zamanı çağrılabilir bir sarmalayıcı oluşturmak için

1. Yönetilen uygulamanız için projeyi açın.

2. **Proje** menüsünde **Tüm Dosyaları Göster'i**tıklatın.

3. **Proje** menüsünde **Referans Ekle'yi**tıklatın.

4. Başvuru Ekle iletişim kutusunda **COM** sekmesini tıklatın, kullanmak istediğiniz bileşeni seçin ve **Tamam'ı**tıklatın.

     **Çözüm Gezgini'nde,** COM bileşeninin projenizdeki Başvurular klasörüne eklenmiştir.

Artık COM nesnesine erişmek için kod yazabilirsiniz. Visual Basic deyimi veya C# için `Imports` bir `Using` deyim gibi nesneyi beyan ederek başlayabilirsiniz.

> [!NOTE]
> Microsoft Office bileşenlerini programlamak istiyorsanız, önce [Microsoft Office Birincil Interop Derlemeleri Yeniden Dağıtılabilir'i yükleyin.](https://www.microsoft.com/Download/details.aspx?id=3508)
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>.NET Framework araçlarını kullanarak çalışma zamanı çağrılabilir sarıcı oluşturmak için  
  
- [Tlbimp.exe (Tip Kitaplığı İthalatçısı)](../tools/tlbimp-exe-type-library-importer.md) aracını çalıştırın.  
  
 Bu araç, özgün tür kitaplığında tanımlanan türler için çalışma zamanı meta verileri içeren bir derleme oluşturur.  
  
## <a name="wrap-managed-objects-in-a-native-application"></a>Yönetilen Nesneleri Yerel Uygulamada Kaydırma  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Visual Studio'u kullanarak com çağrılabilir sarıcı oluşturmak için  
  
1. Yerel kodda çalıştırmak istediğiniz yönetilen sınıf için sınıf kitaplığı projesi oluşturun. Sınıfın parametresiz bir oluşturucusu olmalıdır.  
  
     AssemblyInfo dosyasında assemblyiniz için tam dört bölümlü bir sürüm numarasına sahip olduğunuzu doğrulayın. Bu numara, Windows kayıt defterinde sürüm tutmak için gereklidir. Sürüm numaraları hakkında daha fazla bilgi için [Montaj Sürümü'ne](../../standard/assembly/versioning.md)bakın.  
  
2. **Proje** menüsünde **Özellikler'i**tıklatın.  
  
3. **Derle** sekmesini tıklatın.  
  
4. COM **interop** onay kutusunu kaydedin.  
  
 Projeyi oluşturduğunuzda, derleme otomatik olarak COM interop için kaydedilir. Visual Studio 2005'te yerel bir uygulama oluşturuyorsanız, **Proje** menüsünde **Referans Ekle'yi** tıklatarak derlemeyi kullanabilirsiniz.  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>.NET Framework araçlarını kullanarak com çağrılabilir sarıcı oluşturmak için  
  
[Regasm.exe (Montaj Kayıt Aracı)](../tools/regasm-exe-assembly-registration-tool.md) aracını çalıştırın.  
  
Bu araç derleme meta verilerini okur ve gerekli girişleri kayıt defterine ekler. Sonuç olarak, COM istemcileri .NET Framework sınıflarını saydam olarak oluşturabilir. Derlemeyi yerel bir COM sınıfıymuş gibi kullanabilirsiniz.  
  
Regasm.exe'yi herhangi bir dizinde bulunan bir derlemede çalıştırabilir ve ardından genel derleme önbelleğine taşımak için [Gacutil.exe'yi (Genel Derleme Önbellek Aracı)](../tools/gacutil-exe-gac-tool.md) çalıştırabilirsiniz. Derlemenin taşınması konum kayıt defteri girişlerini geçersiz kılmaz, çünkü derleme başka bir yerde bulunmazsa genel derleme önbelleği her zaman incelenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Aranabilir Sarmalayıcısı](../../standard/native-interop/runtime-callable-wrapper.md)
- [COM Aranabilir Sarmalayıcısı](../../standard/native-interop/com-callable-wrapper.md)
