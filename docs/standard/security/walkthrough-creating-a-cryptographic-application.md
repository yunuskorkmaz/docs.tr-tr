---
title: 'İzlenecek yol: Şifreleme Uygulaması Oluşturma'
description: Bir şifreleme uygulamasının oluşturulmasına yol gösterir. Windows Forms uygulamasındaki içeriği şifrelemeyi ve şifrelerini çözmeyi öğrenin.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET], example
- cryptography [NET], cryptographic application example
- cryptography [NET], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
ms.openlocfilehash: 16a887f23c584daa83106ae61c497bcae8dc4dd2
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557196"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a>İzlenecek yol: Şifreleme Uygulaması Oluşturma

> [!NOTE]
> Bu makale Windows için geçerlidir.
>
> ASP.NET Core hakkında bilgi için bkz. [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).

Bu izlenecek yol, içerik şifrelemesini ve şifresini çözmeyi gösterir. Kod örnekleri, Windows Forms bir uygulama için tasarlanmıştır. Bu uygulama, akıllı kartlar kullanma gibi gerçek dünyada senaryolar göstermez. Bunun yerine, şifreleme ve şifre çözme temellerini gösterir.  
  
Bu izlenecek yol, şifreleme için aşağıdaki yönergeleri kullanır:  
  
- <xref:System.Security.Cryptography.Aes>Otomatik olarak oluşturulan ve kullanarak verileri şifrelemek ve şifrelerini çözmek için simetrik bir algoritma sınıfını kullanın <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> .  
  
- <xref:System.Security.Cryptography.RSA>Tarafından şifrelenen verilerle anahtarı şifrelemek ve şifresini çözmek için asimetrik algoritmayı kullanın <xref:System.Security.Cryptography.Aes> . Asimetrik algoritmalar, anahtar gibi daha küçük miktarlarda veri için en iyi şekilde kullanılır.  
  
    > [!NOTE]
    > Diğer kişilerle şifrelenmiş içerik değişimi yerine bilgisayarınızdaki verileri korumak istiyorsanız, sınıfını kullanmayı düşünün <xref:System.Security.Cryptography.ProtectedData> .  
  
 Aşağıdaki tabloda bu konudaki şifreleme görevleri özetlenmektedir.  
  
|Görev|Açıklama|  
|----------|-----------------|  
|Windows Forms uygulaması oluşturma|Uygulamayı çalıştırmak için gereken denetimleri listeler.|  
|Genel nesneleri bildirme|Dize yol değişkenlerini, <xref:System.Security.Cryptography.CspParameters> ve ' ı <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfının genel bağlamına sahip olacak şekilde bildirir <xref:System.Windows.Forms.Form> .|  
|Asimetrik anahtar oluşturma|Asimetrik ortak ve özel anahtar değer çifti oluşturur ve bir anahtar kapsayıcısı adı atar.|  
|Dosya şifreleme|Şifreleme için bir dosya seçmek üzere bir iletişim kutusu görüntüler ve dosyayı şifreler.|  
|Dosya şifresini çözme|Şifre çözme için şifrelenmiş bir dosya seçmek ve dosyanın şifresini çözmek için bir iletişim kutusu görüntüler.|  
|Özel anahtar alma|Anahtar kapsayıcısı adını kullanarak tam anahtar çiftini alır.|  
|Ortak anahtar dışarı aktarılıyor|Anahtarı yalnızca ortak parametrelere sahip bir XML dosyasına kaydeder.|  
|Ortak anahtar içeri aktarılıyor|Anahtarı bir XML dosyasından anahtar kapsayıcısına yükler.|  
|Uygulamayı test etme|Bu uygulamayı test etmek için yordamları listeler.|  
  
## <a name="prerequisites"></a>Önkoşullar  

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
- <xref:System.IO>Ve <xref:System.Security.Cryptography> ad alanlarına başvurular.  
  
## <a name="creating-a-windows-forms-application"></a>Windows Forms uygulaması oluşturma  

Bu izlenecek yolda bulunan kod örneklerinin çoğu düğme denetimleri için olay işleyicileri olacak şekilde tasarlanmıştır. Aşağıdaki tabloda, örnek uygulama için gereken denetimler ve kod örnekleriyle eşleşmesi için gereken adlar listelenmektedir.  
  
|Denetim|Ad|Metin özelliği (gerektiğinde)|  
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

Bu görev, anahtarı şifreleyen ve şifresini çözdüğü bir asimetrik anahtar oluşturur <xref:System.Security.Cryptography.Aes> . Bu anahtar, içeriği şifrelemek için kullanıldı ve etiket denetimindeki anahtar kapsayıcısı adını görüntülüyor.  
  
 `Click`Düğme () için olay işleyicisi olarak aşağıdaki kodu ekleyin `Create Keys` `buttonCreateAsmKeys_Click` .  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a>Dosya şifreleme  

Bu görev iki yöntem içerir: `Encrypt File` Button ( `buttonEncryptFile_Click` ) ve yöntemi için olay işleyicisi yöntemi `EncryptFile` . İlk yöntem, bir dosya seçmek için bir iletişim kutusu görüntüler ve dosya adını şifrelemeyi gerçekleştiren ikinci yönteme geçirir.  
  
Şifrelenmiş içerik, anahtar ve IV, <xref:System.IO.FileStream> şifreleme paketi olarak adlandırılan tek bir öğesine kaydedilir.  
  
`EncryptFile`Yöntemi aşağıdakileri yapar:  
  
1. <xref:System.Security.Cryptography.Aes>İçeriği şifrelemek için simetrik bir algoritma oluşturur.  
  
2. <xref:System.Security.Cryptography.RSACryptoServiceProvider>Anahtarı şifrelemek için bir nesne oluşturur <xref:System.Security.Cryptography.Aes> .  
  
3. , <xref:System.Security.Cryptography.CryptoStream> <xref:System.IO.FileStream> Kaynak dosyayı, bayt blokları içinde, şifrelenen dosya için bir hedef nesneye okumak ve şifrelemek için bir nesne kullanır <xref:System.IO.FileStream> .  
  
4. Şifrelenmiş anahtarın ve IV 'nin uzunluklarının sayısını belirler ve uzunluk değerlerinin bayt dizilerini oluşturur.  
  
5. Anahtarı, IV ve bunların uzunluk değerlerini şifreli pakete yazar.  
  
 Şifreleme paketi aşağıdaki biçimi kullanır:  
  
- Anahtar uzunluğu, bayt 0-3  
  
- IV uzunluğu, bayt 4-7  
  
- Şifrelenmiş anahtar  
  
- IV  
  
- Şifre metni  
  
 Daha sonra dosyanın şifresini çözmek için kullanılabilecek, şifreleme paketinin tüm bölümlerinin başlangıç noktalarını ve uzunluklarının belirlenmesi için anahtar ve IV uzunluğunu kullanabilirsiniz.  
  
 `Click`Düğme () için olay işleyicisi olarak aşağıdaki kodu ekleyin `Encrypt File` `buttonEncryptFile_Click` .  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 Aşağıdaki `EncryptFile` yöntemi forma ekleyin.  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a>Dosya şifresini çözme  

Bu görev iki yöntem içerir, düğme için olay işleyicisi yöntemi `Decrypt File` ( `buttonDecryptFile_Click` ) ve `DecryptFile` yöntemi. İlk yöntem bir dosya seçmek için bir iletişim kutusu görüntüler ve dosya adını şifre çözme işlemini gerçekleştiren ikinci yönteme geçirir.  
  
`Decrypt`Yöntemi aşağıdakileri yapar:  
  
1. <xref:System.Security.Cryptography.Aes>İçeriğin şifresini çözmek için simetrik bir algoritma oluşturur.  
  
2. Şifrelenmiş <xref:System.IO.FileStream> anahtarın ve IV 'nin uzunluklarının elde etmek için, şifrelenen paketin ilk sekiz baytını bayt dizilerine okur.  
  
3. Anahtar ve IV 'yi şifreleme paketinden bayt dizilerine ayıklar.  
  
4. <xref:System.Security.Cryptography.RSACryptoServiceProvider>Anahtarın şifresini çözmek için bir nesne oluşturur <xref:System.Security.Cryptography.Aes> .  
  
5. <xref:System.Security.Cryptography.CryptoStream> <xref:System.IO.FileStream> Şifreleme paketinin, bayt blokları içindeki şifre metin bölümünü, <xref:System.IO.FileStream> şifresi çözülmüş dosya için nesnesine okumak ve şifresini çözmek için bir nesnesi kullanır. Bu tamamlandığında şifre çözme işlemi tamamlanır.  
  
 `Click`Düğme için olay işleyicisi olarak aşağıdaki kodu ekleyin `Decrypt File` .  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 Aşağıdaki `DecryptFile` yöntemi forma ekleyin.  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a>Ortak anahtar dışarı aktarılıyor

Bu görev düğme tarafından oluşturulan anahtarı `Create Keys` bir dosyaya kaydeder. Yalnızca ortak parametreleri dışarı aktarır.  
  
Bu görev, Gamze 'nin kendi ortak anahtarını veren senaryosuna benzetir. böylece, dosyaları şifreleyebilmesini sağlar. Ortak anahtara sahip olan kişiler ve özel parametrelerle tam anahtar çiftine sahip olmadıkları için şifrelerini çözemeyecektir.  
  
`Click`Düğme () için olay işleyicisi olarak aşağıdaki kodu ekleyin `Export Public Key` `buttonExportPublicKey_Click` .  
  
[!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
[!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a>Ortak anahtar içeri aktarılıyor

Bu görev, anahtarı, düğme tarafından oluşturulan yalnızca ortak parametrelerle yükler `Export Public Key` ve anahtar kapsayıcısı adı olarak ayarlar.  
  
Bu görev, can 'ın, dosyalarını şifreleyebilmesi için Çiğdem 'in anahtarını yalnızca ortak parametrelerle yükleyen emre 'nin senaryosuna benzetir.  
  
`Click`Düğme () için olay işleyicisi olarak aşağıdaki kodu ekleyin `Import Public Key` `buttonImportPublicKey_Click` .  
  
[!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
[!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a>Özel anahtar alma  

Bu görev, anahtar kapsayıcısı adını düğme kullanılarak oluşturulan anahtarın adına ayarlar `Create Keys` . Anahtar kapsayıcısı, özel parametrelerle tam anahtar çiftini içerir.  
  
Bu görev, Bob tarafından şifrelenen dosyaların şifresini çözmek için özel anahtarını kullanarak Gamze 'nin senaryosuna benzetir.  
  
`Click`Düğme () için olay işleyicisi olarak aşağıdaki kodu ekleyin `Get Private Key` `buttonGetPrivateKey_Click` .  
  
[!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
[!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme

Uygulamayı oluşturduktan sonra, aşağıdaki test senaryolarını gerçekleştirin.  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a>Anahtar oluşturmak, şifrelemek ve şifresini çözmek için  
  
1. `Create Keys` düğmesine tıklayın. Etiket, anahtar adını gösterir ve tam bir anahtar çifti olduğunu gösterir.  
  
2. `Export Public Key` düğmesine tıklayın. Ortak anahtar parametrelerini dışa aktarmanın geçerli anahtarı değiştirmediğini unutmayın.  
  
3. Düğmesine tıklayın `Encrypt File` ve bir dosya seçin.  
  
4. Düğmesine tıklayın `Decrypt File` ve yeni şifrelenen dosyayı seçin.  
  
5. Yalnızca şifresi çözülen dosyayı inceleyin.  
  
6. Uygulamayı kapatın ve sonraki senaryoda kalıcı anahtar kapsayıcıları almayı sınamak için yeniden başlatın.  
  
#### <a name="to-encrypt-using-the-public-key"></a>Ortak anahtar kullanarak şifrelemek için  
  
1. `Import Public Key` düğmesine tıklayın. Etiket, anahtar adını görüntüler ve yalnızca ortak olduğunu gösterir.  
  
2. Düğmesine tıklayın `Encrypt File` ve bir dosya seçin.  
  
3. Düğmesine tıklayın `Decrypt File` ve yeni şifrelenen dosyayı seçin. Bu işlem başarısız olur çünkü şifresini çözmek için özel anahtarınız olmalıdır.  
  
 Bu senaryoda, bir dosyayı başka bir kişiye şifrelemek için yalnızca ortak anahtarın bulunması gösterilmektedir. Genellikle bu kişi size yalnızca ortak anahtar verir ve şifre çözme için özel anahtarı karıştı.  
  
#### <a name="to-decrypt-using-the-private-key"></a>Özel anahtarı kullanarak şifresini çözmek için  
  
1. `Get Private Key` düğmesine tıklayın. Etiket, anahtar adını görüntüler ve tam anahtar çifti olup olmadığını gösterir.  
  
2. Düğmesine tıklayın `Decrypt File` ve yeni şifrelenen dosyayı seçin. Şifresini çözmek için tam anahtar çiftine sahip olduğunuzdan bu işlem başarılı olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme modeli](cryptography-model.md) -şifrelemenin temel sınıf kitaplığında nasıl uygulandığını açıklar.
- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)
