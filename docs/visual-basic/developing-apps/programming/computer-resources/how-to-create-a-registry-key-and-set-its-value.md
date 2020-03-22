---
title: 'Nasıl Yapılır: Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama'
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: 459c4b3f971009ee4b6b669c55bc058db0826595
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349195"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama

`My.Computer.Registry` Nesnenin `CreateSubKey` yöntemi bir kayıt defteri anahtarı oluşturmak için kullanılabilir.

## <a name="procedure"></a>Yordam

### <a name="to-create-a-registry-key"></a>Kayıt defteri anahtarı oluşturmak için

- Anahtarın `CreateSubKey` altına hangi kovan yerleştirirken anahtarın adını belirterek yöntemi kullanın. Parametre `Subkey` büyük/küçük harf duyarlı değildir. Bu örnek, HKEY_CURRENT_USER altında `MyTestKey` kayıt defteri anahtarı oluşturur.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Kayıt defteri anahtarı oluşturmak ve içinde bir değer ayarlamak için

1. Anahtarın `CreateSubkey` altına hangi kovan yerleştirirken anahtarın adını belirterek yöntemi kullanın. Bu örnek, HKEY_CURRENT_USER altında `MyTestKey` kayıt defteri anahtarı oluşturur.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. `SetValue` Yöntemi ile değeri ayarlayın. Bu örnek, dize değerini ayarlar. "MyTestKeyValue" için "Bu bir test değeri".

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a>Örnek

Bu örnek, HKEY_CURRENT_USER altında `MyTestKey` kayıt defteri anahtarı nı `MyTestKeyValue` `This is a test value`oluşturur ve dize değerini .

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a>Güçlü Programlama

Anahtarınız için uygun bir yer bulmak için kayıt defteri yapısını inceleyin. Örneğin, geçerli kullanıcının HKEY_CURRENT_USER\Yazılım anahtarını açmak ve şirketinizin adını içeren bir anahtar oluşturmak isteyebilirsiniz. Ardından şirket defteri değerlerini şirketinizin anahtarına ekleyin.

Bir Web uygulamasından kayıt defterini okurken, geçerli kullanıcı Web uygulamasında uygulanan kimlik doğrulama ve kimliğe bürünme bağlıdır.

Yerel bilgisayara () değil, kullanıcı<xref:Microsoft.Win32.Registry.CurrentUser>klasörüne veri yazmak<xref:Microsoft.Win32.Registry.LocalMachine>daha güvenlidir.

Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapacağınız gerektiğine karar vermeniz gerekir. Başka bir işlem, belki de kötü niyetli bir, zaten değer yarattı ve ona erişimi olabilir. Verileri kayıt defteri değerine koyduğunuzda, veriler diğer işlem için kullanılabilir. Bunu önlemek için <xref:Microsoft.Win32.RegistryKey.GetValue%2A> yöntemi kullanın. Anahtar `Nothing` zaten yoksa döndürür.

Kayıt defteri anahtarı ALA'lar (Access Control Lists) tarafından korunsa bile, parolalar gibi sırları kayıt defterinde düz metin olarak depolamak güvenli değildir.

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Anahtarın adı `Nothing` (<xref:System.ArgumentNullException>).

- Kullanıcının kayıt defteri anahtarları oluşturma izinleri<xref:System.Security.SecurityException>yoktur ( ).

- Anahtar adı 255 karakter sınırını aşıyor<xref:System.ArgumentException>( ).

- Anahtar kapalıdır<xref:System.IO.IOException>( ).

- Kayıt defteri anahtarı salt okunur<xref:System.UnauthorizedAccessException>( ).

## <a name="net-framework-security"></a>.NET Framework Güvenliği

Bu işlemi çalıştırmak için derlemeniz <xref:System.Security.Permissions.RegistryPermission> sınıf tarafından verilen bir ayrıcalık düzeyi gerektirir. Kısmi güven bağlamında çalışıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum atabilir. Benzer şekilde, kullanıcının ayarlar oluşturmak veya yazmak için doğru ALA'lara sahip olması gerekir. Örneğin, kod erişim güvenlik iznine sahip yerel bir uygulamanın işletim sistemi izni olmayabilir. Daha fazla bilgi için [Kod Erişim Güvenlik Temelleri'ne](../../../../framework/misc/code-access-security-basics.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Kod Erişim Güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md)
