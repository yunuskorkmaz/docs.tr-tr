---
title: 'Nasıl yapılır: Visual Basic bir kayıt defteri anahtarı oluşturma ve değerini ayarlama'
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
ms.openlocfilehash: 84fc824ad5911621c679d70f480d9b5e83c095ad
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054126"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Nasıl yapılır: Visual Basic bir kayıt defteri anahtarı oluşturma ve değerini ayarlama

`My.Computer.Registry` Nesnesinin yöntemi bir kayıt defteri anahtarı oluşturmak için kullanılabilir. `CreateSubKey`

## <a name="procedure"></a>Yordam

### <a name="to-create-a-registry-key"></a>Kayıt defteri anahtarı oluşturmak için

- Anahtar adının yanı sıra anahtarın altına hangi Hive yerleştirileceğini belirterek yönteminikullanın.`CreateSubKey` Parametre `Subkey` , büyük/küçük harfe duyarlı değildir. Bu örnek, HKEY_CURRENT_USER altında kayıt `MyTestKey` defteri anahtarı oluşturur.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Bir kayıt defteri anahtarı oluşturmak ve içinde bir değer ayarlamak için

1. Anahtar adının yanı sıra anahtarın altına hangi Hive yerleştirileceğini belirterek yönteminikullanın.`CreateSubkey` Bu örnek, HKEY_CURRENT_USER altında kayıt `MyTestKey` defteri anahtarı oluşturur.

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. Değerini `SetValue` yöntemiyle ayarlayın. Bu örnek dize değerini ayarlar. "Bu bir test değeridir" için "MyTestKeyValue".

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a>Örnek

Bu örnekte, HKEY_CURRENT_USER altında kayıt `MyTestKey` defteri anahtarı oluşturulur ve sonra dize değeri `MyTestKeyValue` olarak `This is a test value`ayarlanır.

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a>Güçlü Programlama

Anahtarınız için uygun bir konum bulmak üzere kayıt defteri yapısını inceleyin. Örneğin, geçerli kullanıcının HKEY_CURRENT_USER\Software anahtarını açmak ve şirketinizin adıyla bir anahtar oluşturmak isteyebilirsiniz. Ardından kayıt defteri değerlerini şirketinizin anahtarına ekleyin.

Bir Web uygulamasından kayıt defteri okurken, geçerli kullanıcı Web uygulamasında uygulanan kimlik doğrulamasına ve kimliğe bürünmeye bağlıdır.

Yerel bilgisayar (<xref:Microsoft.Win32.Registry.CurrentUser><xref:Microsoft.Win32.Registry.LocalMachine>) yerine Kullanıcı klasörüne () veri yazmak daha güvenlidir.

Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapılacağını belirlemeniz gerekir. Belki de kötü amaçlı olan bir işlem, değeri zaten oluşturmuş ve ona erişime sahip olabilir. Verileri kayıt defteri değerine yerleştirdiğinizde, veriler diğer işlem tarafından kullanılabilir. Bunu engellemek için <xref:Microsoft.Win32.RegistryKey.GetValue%2A> yöntemini kullanın. Anahtar zaten `Nothing` mevcut değilse döndürür.

Kayıt defteri anahtarı ACL 'Ler (Access Control listeleri) tarafından korunsa bile, parolalar gibi gizli dizileri, kayıt defterinde düz metin olarak depolamak güvenli değildir.

Aşağıdaki koşullar özel bir duruma neden olabilir:

- Anahtarın `Nothing` adı (<xref:System.ArgumentNullException>).

- Kullanıcının kayıt defteri anahtarları oluşturma izni yok (<xref:System.Security.SecurityException>).

- Anahtar adı 255 karakter sınırını (<xref:System.ArgumentException>) aşıyor.

- Anahtar kapalı (<xref:System.IO.IOException>).

- Kayıt defteri anahtarı salt okunurdur (<xref:System.UnauthorizedAccessException>).

## <a name="net-framework-security"></a>.NET Framework Güvenliği

Bu işlemi çalıştırmak için, derlemeniz <xref:System.Security.Permissions.RegistryPermission> sınıf tarafından verilen bir ayrıcalık düzeyi gerektiriyor. Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir. Benzer şekilde, Kullanıcı oluşturma veya ayarları yazma için doğru ACL 'Lere sahip olmalıdır. Örneğin, kod erişim güvenliği iznine sahip bir yerel uygulama işletim sistemi iznine sahip olmayabilir. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../../../framework/misc/code-access-security-basics.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Kod erişim güvenliği temelleri](../../../../framework/misc/code-access-security-basics.md)
