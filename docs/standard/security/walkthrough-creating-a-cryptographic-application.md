---
title: 'İzlenecek Yol: Şifreleme Uygulaması Oluşturma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
ms.openlocfilehash: 6e2d9b8bebdfd2ea5d5507cc73d444fa8bf785fb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705840"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a>İzlenecek Yol: Şifreleme Uygulaması Oluşturma
Bu izlenecek yol, içerik şifrelemesini ve şifresini çözmeyi gösterir. Kod örnekleri, Windows Forms bir uygulama için tasarlanmıştır. Bu uygulama, akıllı kartlar kullanma gibi gerçek dünyada senaryolar göstermez. Bunun yerine, şifreleme ve şifre çözme temellerini gösterir.  
  
 Bu izlenecek yol, şifreleme için aşağıdaki yönergeleri kullanır:  
  
- Otomatik olarak oluşturulan <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> ve <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>kullanarak verileri şifrelemek ve şifrelerini çözmek için <xref:System.Security.Cryptography.RijndaelManaged> sınıfını bir simetrik algoritma kullanın.  
  
- <xref:System.Security.Cryptography.RijndaelManaged>tarafından şifrelenen verilerle anahtarı şifrelemek ve şifresini çözmek için <xref:System.Security.Cryptography.RSACryptoServiceProvider>asimetrik bir algoritma kullanın. Asimetrik algoritmalar, anahtar gibi daha küçük miktarlarda veri için en iyi şekilde kullanılır.  
  
    > [!NOTE]
    > Diğer kişilerle şifrelenmiş içerik alışverişi yerine bilgisayarınızdaki verileri korumak istiyorsanız, <xref:System.Security.Cryptography.ProtectedData> veya <xref:System.Security.Cryptography.ProtectedMemory> sınıflarını kullanmayı düşünün.  
  
 Aşağıdaki tabloda bu konudaki şifreleme görevleri özetlenmektedir.  
  
|Görev|Açıklama|  
|----------|-----------------|  
|Windows Forms uygulaması oluşturma|Uygulamayı çalıştırmak için gereken denetimleri listeler.|  
|Genel nesneleri bildirme|Dize yol değişkenlerini, <xref:System.Security.Cryptography.CspParameters>ve <xref:System.Security.Cryptography.RSACryptoServiceProvider> <xref:System.Windows.Forms.Form> sınıfının genel bağlamına sahip olacak şekilde bildirir.|  
|Asimetrik anahtar oluşturma|Asimetrik ortak ve özel anahtar değer çifti oluşturur ve bir anahtar kapsayıcısı adı atar.|  
|Dosya şifreleme|Şifreleme için bir dosya seçmek üzere bir iletişim kutusu görüntüler ve dosyayı şifreler.|  
|Dosya şifresini çözme|Şifre çözme için şifrelenmiş bir dosya seçmek ve dosyanın şifresini çözmek için bir iletişim kutusu görüntüler.|  
|Özel anahtar alma|Anahtar kapsayıcısı adını kullanarak tam anahtar çiftini alır.|  
|Ortak anahtar dışarı aktarılıyor|Anahtarı yalnızca ortak parametrelere sahip bir XML dosyasına kaydeder.|  
|Ortak anahtar içeri aktarılıyor|Anahtarı bir XML dosyasından anahtar kapsayıcısına yükler.|  
|Uygulamayı test etme|Bu uygulamayı test etmek için yordamları listeler.|  
  
## <a name="prerequisites"></a>Prerequisites  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
- <xref:System.IO> ve <xref:System.Security.Cryptography> ad alanlarına başvurular.  
  
## <a name="creating-a-windows-forms-application"></a>Windows Forms uygulaması oluşturma  
 Bu izlenecek yolda bulunan kod örneklerinin çoğu düğme denetimleri için olay işleyicileri olacak şekilde tasarlanmıştır. Aşağıdaki tabloda, örnek uygulama için gereken denetimler ve kod örnekleriyle eşleşmesi için gereken adlar listelenmektedir.  
  
|Denetim|Name|Metin özelliği (gerektiğinde)|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|Dosyayı şifreleyin|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|Dosya şifresini çöz|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|Anahtar oluştur|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|Ortak anahtarı dışarı aktar|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|Ortak anahtarı içeri aktar|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|Özel anahtar al|  
|<xref:System.Windows.Forms.Label>|`label1`|Anahtar ayarlanmadı|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 Olay işleyicilerini oluşturmak için Visual Studio tasarımcısında düğmelere çift tıklayın.  
  
## <a name="declaring-global-objects"></a>Genel nesneleri bildirme  
 Form yapıcısına aşağıdaki kodu ekleyin. Ortamınız ve tercihleriniz için dize değişkenlerini düzenleyin.  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a>Asimetrik anahtar oluşturma  
 Bu görev <xref:System.Security.Cryptography.RijndaelManaged> anahtarını şifreleyen ve şifresini çözdüğü bir asimetrik anahtar oluşturur. Bu anahtar, içeriği şifrelemek için kullanıldı ve etiket denetimindeki anahtar kapsayıcısı adını görüntülüyor.  
  
 Aşağıdaki kodu `Create Keys` düğmesi için `Click` olay işleyicisi olarak ekleyin (`buttonCreateAsmKeys_Click`).  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a>Dosya şifreleme  
 Bu görev iki yöntem içerir: `Encrypt File` düğmenin (`buttonEncryptFile_Click`) ve `EncryptFile` yönteminin olay işleyicisi yöntemi. İlk yöntem, bir dosya seçmek için bir iletişim kutusu görüntüler ve dosya adını şifrelemeyi gerçekleştiren ikinci yönteme geçirir.  
  
 Şifrelenmiş içerik, anahtar ve IV, şifreleme paketi olarak adlandırılan tek bir <xref:System.IO.FileStream>kaydedilir.  
  
 `EncryptFile` yöntemi aşağıdakileri yapar:  
  
1. İçeriği şifrelemek için <xref:System.Security.Cryptography.RijndaelManaged> simetrik bir algoritma oluşturur.  
  
2. <xref:System.Security.Cryptography.RijndaelManaged> anahtarını şifrelemek için bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesnesi oluşturur.  
  
3. , Kaynak dosyanın <xref:System.IO.FileStream> bayt blokları içinde, şifrelenen dosya için hedef <xref:System.IO.FileStream> nesnesine okumak ve şifrelemek için bir <xref:System.Security.Cryptography.CryptoStream> nesnesi kullanır.  
  
4. Şifrelenmiş anahtarın ve IV 'nin uzunluklarının sayısını belirler ve uzunluk değerlerinin bayt dizilerini oluşturur.  
  
5. Anahtarı, IV ve bunların uzunluk değerlerini şifreli pakete yazar.  
  
 Şifreleme paketi aşağıdaki biçimi kullanır:  
  
- Anahtar uzunluğu, bayt 0-3  
  
- IV uzunluğu, bayt 4-7  
  
- Şifrelenmiş anahtar  
  
- IV  
  
- Şifre metni  
  
 Daha sonra dosyanın şifresini çözmek için kullanılabilecek, şifreleme paketinin tüm bölümlerinin başlangıç noktalarını ve uzunluklarının belirlenmesi için anahtar ve IV uzunluğunu kullanabilirsiniz.  
  
 Aşağıdaki kodu `Encrypt File` düğmesi için `Click` olay işleyicisi olarak ekleyin (`buttonEncryptFile_Click`).  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 Aşağıdaki `EncryptFile` yöntemini forma ekleyin.  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a>Dosya şifresini çözme  
 Bu görev, `Decrypt File` düğmesi (`buttonDecryptFile_Click`) ve `DecryptFile` yöntemi için olay işleyicisi yöntemi olmak üzere iki yöntem içerir. İlk yöntem bir dosya seçmek için bir iletişim kutusu görüntüler ve dosya adını şifre çözme işlemini gerçekleştiren ikinci yönteme geçirir.  
  
 `Decrypt` yöntemi aşağıdakileri yapar:  
  
1. İçeriğin şifresini çözmek için <xref:System.Security.Cryptography.RijndaelManaged> simetrik bir algoritma oluşturur.  
  
2. Şifrelenmiş anahtarın ve IV 'nin uzunluklarının elde edileceği şekilde, şifrelenmiş paketin <xref:System.IO.FileStream> ilk sekiz baytını bayt dizileri olarak okur.  
  
3. Anahtar ve IV 'yi şifreleme paketinden bayt dizilerine ayıklar.  
  
4. <xref:System.Security.Cryptography.RijndaelManaged> anahtarının şifresini çözmek için bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesnesi oluşturur.  
  
5. , <xref:System.IO.FileStream> şifreleme paketinin şifreleme metni bölümünü, şifresi çözülmüş dosyanın <xref:System.IO.FileStream> nesnesine okumak ve şifresini çözmek için bir <xref:System.Security.Cryptography.CryptoStream> nesnesi kullanır. Bu tamamlandığında şifre çözme işlemi tamamlanır.  
  
 Aşağıdaki kodu `Decrypt File` düğmesi için `Click` olay işleyicisi olarak ekleyin.  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 Aşağıdaki `DecryptFile` yöntemini forma ekleyin.  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a>Ortak anahtar dışarı aktarılıyor  
 Bu görev `Create Keys` düğmesi tarafından oluşturulan anahtarı bir dosyaya kaydeder. Yalnızca ortak parametreleri dışarı aktarır.  
  
 Bu görev, Gamze 'nin kendi ortak anahtarını veren senaryosuna benzetir. böylece, dosyaları şifreleyebilmesini sağlar. Ortak anahtara sahip olan kişiler ve özel parametrelerle tam anahtar çiftine sahip olmadıkları için şifrelerini çözemeyecektir.  
  
 Aşağıdaki kodu `Export Public Key` düğmesi için `Click` olay işleyicisi olarak ekleyin (`buttonExportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a>Ortak anahtar içeri aktarılıyor  
 Bu görev, anahtarı `Export Public Key` düğmesi tarafından oluşturulan yalnızca ortak parametrelerle yükler ve anahtar kapsayıcısı adı olarak ayarlar.  
  
 Bu görev, can 'ın, dosyalarını şifreleyebilmesi için Çiğdem 'in anahtarını yalnızca ortak parametrelerle yükleyen emre 'nin senaryosuna benzetir.  
  
 Aşağıdaki kodu `Import Public Key` düğmesi için `Click` olay işleyicisi olarak ekleyin (`buttonImportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a>Özel anahtar alma  
 Bu görev, `Create Keys` düğmesini kullanarak anahtar kapsayıcısı adını oluşturulan anahtarın adına ayarlar. Anahtar kapsayıcısı, özel parametrelerle tam anahtar çiftini içerir.  
  
 Bu görev, Bob tarafından şifrelenen dosyaların şifresini çözmek için özel anahtarını kullanarak Gamze 'nin senaryosuna benzetir.  
  
 Aşağıdaki kodu `Get Private Key` düğmesi için `Click` olay işleyicisi olarak ekleyin (`buttonGetPrivateKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Uygulamayı oluşturduktan sonra, aşağıdaki test senaryolarını gerçekleştirin.  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a>Anahtar oluşturmak, şifrelemek ve şifresini çözmek için  
  
1. `Create Keys` düğmesine tıklayın. Etiket, anahtar adını gösterir ve tam bir anahtar çifti olduğunu gösterir.  
  
2. `Export Public Key` düğmesine tıklayın. Ortak anahtar parametrelerini dışa aktarmanın geçerli anahtarı değiştirmediğini unutmayın.  
  
3. `Encrypt File` düğmesine tıklayın ve bir dosya seçin.  
  
4. `Decrypt File` düğmesine tıklayın ve yeni şifrelenen dosyayı seçin.  
  
5. Yalnızca şifresi çözülen dosyayı inceleyin.  
  
6. Uygulamayı kapatın ve sonraki senaryoda kalıcı anahtar kapsayıcıları almayı sınamak için yeniden başlatın.  
  
#### <a name="to-encrypt-using-the-public-key"></a>Ortak anahtar kullanarak şifrelemek için  
  
1. `Import Public Key` düğmesine tıklayın. Etiket, anahtar adını görüntüler ve yalnızca ortak olduğunu gösterir.  
  
2. `Encrypt File` düğmesine tıklayın ve bir dosya seçin.  
  
3. `Decrypt File` düğmesine tıklayın ve yeni şifrelenen dosyayı seçin. Bu işlem başarısız olur çünkü şifresini çözmek için özel anahtarınız olmalıdır.  
  
 Bu senaryoda, bir dosyayı başka bir kişiye şifrelemek için yalnızca ortak anahtarın bulunması gösterilmektedir. Genellikle bu kişi size yalnızca ortak anahtar verir ve şifre çözme için özel anahtarı karıştı.  
  
#### <a name="to-decrypt-using-the-private-key"></a>Özel anahtarı kullanarak şifresini çözmek için  
  
1. `Get Private Key` düğmesine tıklayın. Etiket, anahtar adını görüntüler ve tam anahtar çifti olup olmadığını gösterir.  
  
2. `Decrypt File` düğmesine tıklayın ve yeni şifrelenen dosyayı seçin. Şifresini çözmek için tam anahtar çiftine sahip olduğunuzdan bu işlem başarılı olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
