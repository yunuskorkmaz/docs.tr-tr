---
title: Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 513000169504473aa6dd46feaca214f58502ffd0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69912864"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a><span data-ttu-id="3e20b-102">Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="3e20b-102">Mapping Algorithm Names to Cryptography Classes</span></span>
<span data-ttu-id="3e20b-103">Bir geliştiricinin Windows SDK kullanarak bir şifreleme nesnesi oluştur, dört yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="3e20b-103">There are four ways a developer can create a cryptography object using the Windows SDK:</span></span>  
  
- <span data-ttu-id="3e20b-104">**New** işlecini kullanarak bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e20b-104">Create an object by using the **new** operator.</span></span>  
  
- <span data-ttu-id="3e20b-105">Bu algoritmanın soyut sınıfında **Create** yöntemini çağırarak belirli bir şifreleme algoritmasını uygulayan bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e20b-105">Create an object that implements a particular cryptography algorithm by calling the **Create** method on the abstract class for that algorithm.</span></span>  
  
- <span data-ttu-id="3e20b-106">Yöntemini çağırarak belirli bir şifreleme algoritmasını uygulayan bir nesne oluşturun <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3e20b-106">Create an object that implements a particular cryptography algorithm by calling the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="3e20b-107">Bir şifreleme algoritmaları sınıfı (simetrik blok şifresi gibi) uygulayan bir nesne oluşturun (örneğin,) bu tür algoritma için soyut sınıfta **Create** yöntemini çağırarak <xref:System.Security.Cryptography.SymmetricAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="3e20b-107">Create an object that implements a class of cryptographic algorithms (such as a symmetric block cipher) by calling the **Create** method on the abstract class for that type of algorithm (such as <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span></span>  
  
 <span data-ttu-id="3e20b-108">Örneğin, bir geliştiricinin bir bayt kümesinin SHA1 karmasını hesaplamak istediğini varsayalım.</span><span class="sxs-lookup"><span data-stu-id="3e20b-108">For example, suppose a developer wants to compute the SHA1 hash of a set of bytes.</span></span> <span data-ttu-id="3e20b-109"><xref:System.Security.Cryptography>Ad alanı, tek bir yönetilen uygulama ve CryptoAPI 'yi sarmalayan BIR SHA1 algoritmasının iki uygulamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="3e20b-109">The <xref:System.Security.Cryptography> namespace contains two implementations of the SHA1 algorithm, one purely managed implementation and one that wraps CryptoAPI.</span></span> <span data-ttu-id="3e20b-110">Geliştirici, <xref:System.Security.Cryptography.SHA1Managed> **Yeni** işleci ÇAĞıRARAK belirli bir SHA1 uygulamasının (örneğin,) örneğini oluşturmaya seçim yapabilir.</span><span class="sxs-lookup"><span data-stu-id="3e20b-110">The developer can choose to instantiate a particular SHA1 implementation (such as the <xref:System.Security.Cryptography.SHA1Managed>) by calling the **new** operator.</span></span> <span data-ttu-id="3e20b-111">Ancak, sınıf, SHA1 karma algoritmasını uyguladığı sürece ortak dil çalışma zamanının hangi sınıftan yüklendiğine bakılmaksızın, geliştirici yöntemini çağırarak bir nesne oluşturabilir <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3e20b-111">However, if it does not matter which class the common language runtime loads as long as the class implements the SHA1 hash algorithm, the developer can create an object by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3e20b-112">Bu yöntem, SHA1 karma algoritmasının bir uygulamasını döndürmesi gereken **System. Security. Cryptography. CryptoConfig. CreateFromName ("System. Security. Cryptography. SHA1")** öğesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="3e20b-112">This method calls **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, which must return an implementation of the SHA1 hash algorithm.</span></span>  
  
 <span data-ttu-id="3e20b-113">Geliştirici, varsayılan olarak, .NET Framework gelen algoritmaların kısa adlarını içerdiğinden, **sistem. Security. Cryptography. CryptoConfig. CreateFromName ("SHA1")** öğesini de çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="3e20b-113">The developer can also call **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** because, by default, cryptography configuration includes short names for the algorithms shipped in the .NET Framework.</span></span>  
  
 <span data-ttu-id="3e20b-114">Hangi karma algoritmanın kullanıldığına bakılmaksızın geliştirici, <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> karma dönüşüm uygulayan bir nesne döndüren yöntemini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="3e20b-114">If it does not matter which hash algorithm is used, the developer can call the <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> method, which returns an object that implements a hashing transformation.</span></span>  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a><span data-ttu-id="3e20b-115">Yapılandırma dosyalarında algoritma adlarını eşleme</span><span class="sxs-lookup"><span data-stu-id="3e20b-115">Mapping Algorithm Names in Configuration Files</span></span>  
 <span data-ttu-id="3e20b-116">Varsayılan olarak, çalışma zamanı <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> dört senaryo için bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e20b-116">By default, the runtime returns a <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> object for all four scenarios.</span></span> <span data-ttu-id="3e20b-117">Ancak, bir makine Yöneticisi son iki senaryodaki yöntemlerin döndürdüğü nesne türünü değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="3e20b-117">However, a machine administrator can change the type of object that the methods in the last two scenarios return.</span></span> <span data-ttu-id="3e20b-118">Bunu yapmak için, bir kolay algoritma adını makine yapılandırma dosyasında (Machine. config) kullanmak istediğiniz sınıfa eşlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e20b-118">To do this, you must map a friendly algorithm name to the class you want to use in the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="3e20b-119">Aşağıdaki örnek, **System. Security. Cryptography. SHA1. Create**, **System. Security. CryptoConfig. CreateFromName ("SHA1")** ve **System. Security. Cryptography. HashAlgorithm. Create** için bir nesne döndürmesi amacıyla çalışma zamanının nasıl yapılandırılacağını gösterir `MySHA1HashClass` .</span><span class="sxs-lookup"><span data-stu-id="3e20b-119">The following example shows how to configure the runtime so that **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, and **System.Security.Cryptography.HashAlgorithm.Create** return a `MySHA1HashClass` object.</span></span>  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="3e20b-120">[<cryptoClass \> öğesinde](./file-schema/cryptography/cryptoclass-element.md) özniteliğin adını belirtebilirsiniz (önceki örnek, özniteliğini adlandırır `MySHA1Hash` ).</span><span class="sxs-lookup"><span data-stu-id="3e20b-120">You can specify the name of the attribute in the [<cryptoClass\> element](./file-schema/cryptography/cryptoclass-element.md) (the previous example names the attribute `MySHA1Hash`).</span></span> <span data-ttu-id="3e20b-121">Öğesindeki özniteliğin değeri, **\<cryptoClass>** ortak dil çalışma zamanının sınıfı bulmak için kullandığı bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="3e20b-121">The value of the attribute in the **\<cryptoClass>** element is a string that the common language runtime uses to find the class.</span></span> <span data-ttu-id="3e20b-122">[Tam nitelikli tür adlarını belirtirken](../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan herhangi bir dizeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e20b-122">You can use any string that meets the requirements specified in [Specifying Fully Qualified Type Names](../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>  
  
 <span data-ttu-id="3e20b-123">Birçok algoritma adı aynı sınıfa eşleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3e20b-123">Many algorithm names can map to the same class.</span></span> <span data-ttu-id="3e20b-124">[ \<nameEntry> Öğesi](./file-schema/cryptography/nameentry-element.md) bir sınıfı bir kolay algoritma adıyla eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="3e20b-124">The [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md) maps a class to one friendly algorithm name.</span></span> <span data-ttu-id="3e20b-125">**Name** özniteliği, **System. Security. Cryptography. CryptoConfig. CreateFromName** yöntemi veya ad alanındaki bir soyut şifreleme sınıfının adı çağrılırken kullanılan bir dize olabilir <xref:System.Security.Cryptography> .</span><span class="sxs-lookup"><span data-stu-id="3e20b-125">The **name** attribute can be either a string that is used when calling the **System.Security.Cryptography.CryptoConfig.CreateFromName** method or the name of an abstract cryptography class in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="3e20b-126">**Sınıf** özniteliğinin değeri, öğesindeki özniteliğin adıdır **\<cryptoClass>** .</span><span class="sxs-lookup"><span data-stu-id="3e20b-126">The value of the **class** attribute is the name of the attribute in the **\<cryptoClass>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e20b-127"><xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>Veya **Security. CryptoConfig. CreateFromName ("SHA1")** YÖNTEMINI çağırarak bir SHA1 algoritması edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e20b-127">You can get an SHA1 algorithm by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> or the **Security.CryptoConfig.CreateFromName("SHA1")** method.</span></span> <span data-ttu-id="3e20b-128">Her yöntem yalnızca SHA1 algoritmasını uygulayan bir nesne döndüren garantisi verir.</span><span class="sxs-lookup"><span data-stu-id="3e20b-128">Each method guarantees only that it returns an object that implements the SHA1 algorithm.</span></span> <span data-ttu-id="3e20b-129">Bir algoritmaların kolay adlarını yapılandırma dosyasındaki aynı sınıfa eşlemek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e20b-129">You do not have to map each friendly name of an algorithm to the same class in the configuration file.</span></span>  
  
 <span data-ttu-id="3e20b-130">Varsayılan adların ve eşlendikleri sınıfların listesi için bkz <xref:System.Security.Cryptography.CryptoConfig> ..</span><span class="sxs-lookup"><span data-stu-id="3e20b-130">For a list of default names and the classes they map to, see <xref:System.Security.Cryptography.CryptoConfig>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e20b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e20b-131">See also</span></span>

- [<span data-ttu-id="3e20b-132">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="3e20b-132">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="3e20b-133">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3e20b-133">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
