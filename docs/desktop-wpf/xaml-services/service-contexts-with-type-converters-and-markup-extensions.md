---
title: Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 59c4385eb4df8c622be6164cdb0a1a911c445ca8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071663"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a><span data-ttu-id="8d7d4-102">Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları</span><span class="sxs-lookup"><span data-stu-id="8d7d4-102">Service Contexts Available to Type Converters and Markup Extensions</span></span>
<span data-ttu-id="8d7d4-103">Tür dönüştürücü ve biçimlendirme uzantısı kullanımlarını destekleyen türlerin yazarlarıgenellikle biçimlendirmede veya çevreleyen nesne grafiği yapısında bir kullanımın nerede bulunduğu hakkında bağlamsal bilgilere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-103">Authors of the types that support type converter and markup extension usages must often have contextual information about where a usage is located in the markup, or in surrounding object graph structure.</span></span> <span data-ttu-id="8d7d4-104">Sağlanan nesnenin doğru bir şekilde anlık olarak anlık olarak veya nesne grafiğindeki varolan nesnelere nesne başvuruları yapılabilecek şekilde bilgi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-104">Information might be needed so that the provided object is instantiated correctly or so that object references to existing objects in the object graph can be made.</span></span> <span data-ttu-id="8d7d4-105">.NET XAML Hizmetleri kullanırken, gerekli olabilecek bağlam bir dizi hizmet arabirimi olarak ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-105">When using .NET XAML Services, the context that might be required is exposed as a series of service interfaces.</span></span> <span data-ttu-id="8d7d4-106">Tür dönüştürücü veya biçimlendirme uzantısı destek kodu, kullanılabilir ve kullanılabilir ve ilgili <xref:System.Xaml.XamlObjectWriter> türler veya ilgili türler aracılığıyla geçirilen bir hizmet sağlayıcı bağlamı kullanarak bir hizmet için sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-106">Type converter or markup extension support code can query for a service by using a service provider context that is available and passed through from <xref:System.Xaml.XamlObjectWriter> or related types.</span></span> <span data-ttu-id="8d7d4-107">XAML şeması bağlamı doğrudan böyle bir hizmet aracılığıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-107">The XAML schema context is directly available through one such service.</span></span> <span data-ttu-id="8d7d4-108">Bu konu, bir değer dönüştürücü uygulamasından hizmet bağlamlarına nasıl erişilenleri açıklar ve genellikle kullanılabilir hizmetleri ve bunların rollerini listeler.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-108">This topic describes how to access service contexts from a value converter implementation, and lists typically available services and their roles.</span></span>

## <a name="obtaining-services"></a><span data-ttu-id="8d7d4-109">Hizmet Alma</span><span class="sxs-lookup"><span data-stu-id="8d7d4-109">Obtaining Services</span></span>

<span data-ttu-id="8d7d4-110">Bir değer dönüştürücüsünün uygulayıcısı olarak, genellikle değer dönüştürücünün uygulandığı bir tür içeriğe erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-110">As an implementer of a value converter, you often need access to some type of context in which the value converter is applied.</span></span> <span data-ttu-id="8d7d4-111">Bu bağlam, etkin XAML şeması bağlamı, XAML şema bağlamı ve XAML nesne yazarının sağladığı tür eşleme sistemine erişim ve benzeri bilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-111">This context might include information such as the active XAML schema context, access to the type-mapping system that the XAML schema context and XAML object writer provide, and so on.</span></span> <span data-ttu-id="8d7d4-112">Biçimlendirme uzantısı veya tür dönüştürücü uygulaması için kullanılabilen hizmetler, her sanal yöntemin imzasının bir parçası olan bağlam parametreleri aracılığıyla iletilir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-112">The services available for a markup extension or type converter implementation are communicated through the context parameters that are part of the signature of each virtual method.</span></span> <span data-ttu-id="8d7d4-113">Her durumda, bağlamında <xref:System.IServiceProvider> uyguladınız ve bir hizmet <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> istemek için arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-113">In every case, you have <xref:System.IServiceProvider> implemented in the context, and can call <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> to request a service.</span></span>

## <a name="services-for-a-markup-extension"></a><span data-ttu-id="8d7d4-114">Biçimlendirme Uzantısı Için Hizmetler</span><span class="sxs-lookup"><span data-stu-id="8d7d4-114">Services for a Markup Extension</span></span>

<span data-ttu-id="8d7d4-115"><xref:System.Windows.Markup.MarkupExtension>yalnızca bir sanal <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-115"><xref:System.Windows.Markup.MarkupExtension> has only one virtual method, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>.</span></span> <span data-ttu-id="8d7d4-116">Giriş `serviceProvider` parametresi, biçimlendirme uzantısı xaml işlemci tarafından çağrıldığında hizmetlerin uygulamalara nasıl iletildiğidir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-116">The input `serviceProvider` parameter is how the services are communicated to implementations when the markup extension is called by a XAML processor.</span></span> <span data-ttu-id="8d7d4-117">Aşağıdaki pseudocode, biçimlendirme uzantısı uygulamasının aşağıdaki <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>hizmetler için nasıl sorgulayabildiğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="8d7d4-117">The following pseudocode illustrates how a markup extension implementation might query for services in its <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>:</span></span>

```csharp
public override object ProvideValue(IServiceProvider serviceProvider)
{
...
    // Get the IXamlTypeResolver from the service provider
    if (serviceProvider == null)
    {
        throw new ArgumentNullException("serviceProvider");
    }
    IXamlTypeResolver xamlTypeResolver = serviceProvider.GetService(typeof(IXamlTypeResolver)) as IXamlTypeResolver;
    if (xamlTypeResolver == null)
   {
        throw new ArgumentException("IXamlTypeResolver"));
    }
...
}
```

## <a name="services-for-a-type-converter"></a><span data-ttu-id="8d7d4-118">Tip Dönüştürücü için Hizmetler</span><span class="sxs-lookup"><span data-stu-id="8d7d4-118">Services for a Type Converter</span></span>

<span data-ttu-id="8d7d4-119"><xref:System.ComponentModel.TypeConverter>bir hizmet bağlamı kullanan ve XAML kullanımlarını destekleyen dört sanal yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-119"><xref:System.ComponentModel.TypeConverter> has four virtual methods that use a service context and that support XAML usages.</span></span> <span data-ttu-id="8d7d4-120">Bu yöntemlerin her biri `context` bir giriş parametresi geçer.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-120">Each of these methods passes an input `context` parameter.</span></span> <span data-ttu-id="8d7d4-121">Bu parametre türü, <xref:System.ComponentModel.ITypeDescriptorContext>ancak bu <xref:System.IServiceProvider>arabirim devralır , <xref:System.IServiceProvider.GetService%2A> ve bu nedenle, dönüştürücü uygulamaları yazmak için kullanılabilir bir yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-121">This parameter is of type <xref:System.ComponentModel.ITypeDescriptorContext>, but that interface inherits <xref:System.IServiceProvider>, and therefore, there is a <xref:System.IServiceProvider.GetService%2A> method available to type converter implementations.</span></span>

<span data-ttu-id="8d7d4-122">Aşağıdaki pseudocode, XAML kullanımları için bir tür dönüştürücü uygulamasının, bu durumda, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>geçersiz kılardan birinde hizmetleri nasıl sorgulayabildiğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="8d7d4-122">The following pseudocode illustrates how a type converter implementation for XAML usages might query for services in one of its overrides, in this case <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>:</span></span>

```csharp
public override object ConvertFrom(ITypeDescriptorContext typeDescriptorContext,
  CultureInfo cultureInfo,
  object source)
{
    IRootObjectProvider rootProvider = typeDescriptorContext.GetService(typeof(IRootObjectProvider)) as IRootObjectProvider;
    if (rootProvider != null && source is String)
    {
        //return something, else ...
    }
    throw GetConvertFromException(source);
}
```

## <a name="services-for-a-value-serializer"></a><span data-ttu-id="8d7d4-123">Değer Serializer için Hizmetler</span><span class="sxs-lookup"><span data-stu-id="8d7d4-123">Services for a Value Serializer</span></span>

<span data-ttu-id="8d7d4-124">Değer serileştirici bağlamı için, <xref:System.Windows.Markup.ValueSerializer> sınıfa özgü bir hizmet <xref:System.Windows.Markup.IValueSerializerContext>sağlayıcı türü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-124">For value serializer context, you use a service provider type that is specific to the <xref:System.Windows.Markup.ValueSerializer> class, <xref:System.Windows.Markup.IValueSerializerContext>.</span></span> <span data-ttu-id="8d7d4-125">Bu bağlam, dört <xref:System.Windows.Markup.ValueSerializer> sanal yöntemin geçersiz kılmalarına aktarılır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-125">That context is passed to overrides of the four <xref:System.Windows.Markup.ValueSerializer> virtual methods.</span></span> <span data-ttu-id="8d7d4-126">Hizmet <xref:System.IServiceProvider.GetService%2A> almak için bağlamdan arayın.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-126">Call <xref:System.IServiceProvider.GetService%2A> from the context to obtain services.</span></span>

## <a name="using-the-xaml-service-provider-contexts"></a><span data-ttu-id="8d7d4-127">XAML Servis Sağlayıcı Bağlamlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="8d7d4-127">Using the XAML Service Provider Contexts</span></span>

<span data-ttu-id="8d7d4-128">Uzantıları veya <xref:System.IServiceProvider.GetService%2A> tür dönüştürücüleri işaretlemek için kullanılabilen XAML hizmetlerine erişim için hizmet sağlayıcısı, yalnızca arabirim üzerinden ve ilgili içeriğe nasıl aktarılan bir iç sınıf olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-128">The service provider for <xref:System.IServiceProvider.GetService%2A> access to XAML services available to markup extensions or type converters is implemented as an internal class, with exposure only through the interface and how it is passed into the relevant context.</span></span> <span data-ttu-id="8d7d4-129">Yük yolunun varsayılan .NET XAML Hizmetleri uygulamalarında bir XAML işleme işlemi, bir hizmet bağlamı gerektiren ilgili biçimlendirme uzantısı veya tür dönüştürücü yöntemlerini çağırdığında, bu iç nesne geçirilir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-129">Whenever a XAML processing operation in the default .NET XAML Services implementations of load path or save path invokes the relevant markup extension or type converter methods that require a service context, this internal object is passed.</span></span> <span data-ttu-id="8d7d4-130">Duruma bağlı olarak, sistem hizmeti bağlamı sağlar `MarkupExtensionContext` ya da `TextSyntaxContext`, ancak bu sınıfların her ikisinin özellikleri iç.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-130">Depending on the circumstance, the system service context provides either `MarkupExtensionContext` or `TextSyntaxContext`, but the specifics of both of these classes are internal.</span></span> <span data-ttu-id="8d7d4-131">Bu sınıflarla etkileşiminiz, onlardan hizmet istemekle <xref:System.IServiceProvider.GetService%2A>sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-131">Your interaction with these classes is limited to requesting services from them, through <xref:System.IServiceProvider.GetService%2A>.</span></span>

## <a name="available-services-from-the-net-xaml-service-context"></a><span data-ttu-id="8d7d4-132">.NET XAML Hizmet Bağlamından Mevcut Hizmetler</span><span class="sxs-lookup"><span data-stu-id="8d7d4-132">Available Services from the .NET XAML Service Context</span></span>

<span data-ttu-id="8d7d4-133">.NET XAML Hizmetleri, biçimlendirme uzantıları, tür dönüştürücüler, değer serileştiricileri ve potansiyel olarak diğer kullanımlar için hizmetleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-133">.NET XAML Services defines services for markup extensions, type converters, value serializers, and potentially other usages.</span></span> <span data-ttu-id="8d7d4-134">Aşağıdaki bölümler, bu hizmetlerin her birini açıklar ve hizmetin bir uygulamada nasıl kullanılabileceği hakkında rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-134">The following sections describe each of these services and provide guidance about how the service might be used in an implementation.</span></span>

### <a name="iserviceprovider"></a><span data-ttu-id="8d7d4-135">ıserviceprovider</span><span class="sxs-lookup"><span data-stu-id="8d7d4-135">IServiceProvider</span></span>

<span data-ttu-id="8d7d4-136">**Referans belgeleri**:<xref:System.IServiceProvider></span><span class="sxs-lookup"><span data-stu-id="8d7d4-136">**Reference documentation**: <xref:System.IServiceProvider></span></span>

<span data-ttu-id="8d7d4-137">**İlgili:** .NET'te hizmet tabanlı bir altyapının temel <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>çalışması, böylece .</span><span class="sxs-lookup"><span data-stu-id="8d7d4-137">**Relevant to:** Basic operation of a service-based infrastructure in .NET so that you can call <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.</span></span>

### <a name="itypedescriptorcontext"></a><span data-ttu-id="8d7d4-138">ıtypedescriptorcontext</span><span class="sxs-lookup"><span data-stu-id="8d7d4-138">ITypeDescriptorContext</span></span>

<span data-ttu-id="8d7d4-139">**Referans belgeleri**:<xref:System.ComponentModel.ITypeDescriptorContext></span><span class="sxs-lookup"><span data-stu-id="8d7d4-139">**Reference documentation**: <xref:System.ComponentModel.ITypeDescriptorContext></span></span>

<span data-ttu-id="8d7d4-140"><xref:System.IServiceProvider>Türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-140">Derives from <xref:System.IServiceProvider>.</span></span> <span data-ttu-id="8d7d4-141">Bu sınıf, standart <xref:System.ComponentModel.TypeConverter> imzalarda bağlamı temsil eder; <xref:System.ComponentModel.TypeConverter> .NET Framework 1.0'dan beri var olan bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-141">This class represents context in the standard <xref:System.ComponentModel.TypeConverter> signatures; <xref:System.ComponentModel.TypeConverter> is a class that has existed since .NET Framework 1.0.</span></span> <span data-ttu-id="8d7d4-142">Dize değeri türü dönüştürme için <xref:System.ComponentModel.TypeConverter> XAML ve XAML senaryosundan önce uzanır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-142">It predates XAML and the XAML <xref:System.ComponentModel.TypeConverter> scenario for string-value type conversion.</span></span> <span data-ttu-id="8d7d4-143">.NET XAML Hizmetleri bağlamında, <xref:System.ComponentModel.TypeConverter> yöntemleri açıkça uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-143">In .NET XAML Services context, methods of <xref:System.ComponentModel.TypeConverter> are implemented explicitly.</span></span> <span data-ttu-id="8d7d4-144">Açık uygulamanın davranışı, arayanlara API'nin <xref:System.ComponentModel.ITypeDescriptorContext> XAML türü sistemleri yle veya XAML'den nesneleri okumak veya yazmak için uygun olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-144">The explicit implementation's behavior indicates to callers that the <xref:System.ComponentModel.ITypeDescriptorContext> API is not relevant for XAML type systems, or for reading or writing objects from XAML.</span></span> <span data-ttu-id="8d7d4-145"><xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>ve <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> genellikle `null` .NET XAML Hizmetleri bağlamlarından döner.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-145"><xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>, and <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> generally return `null` from .NET XAML Services contexts.</span></span>

### <a name="ivalueserializercontext"></a><span data-ttu-id="8d7d4-146">ıvalueserializercontext</span><span class="sxs-lookup"><span data-stu-id="8d7d4-146">IValueSerializerContext</span></span>

<span data-ttu-id="8d7d4-147">**Referans belgeleri**:<xref:System.Windows.Markup.IValueSerializerContext></span><span class="sxs-lookup"><span data-stu-id="8d7d4-147">**Reference documentation**: <xref:System.Windows.Markup.IValueSerializerContext></span></span>

<span data-ttu-id="8d7d4-148">XAML <xref:System.ComponentModel.ITypeDescriptorContext> türü sistemi hakkında yanlış etkileri bastırmak için açık uygulamalardan türetilmiştir ve ayrıca dayanır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-148">Derives from <xref:System.ComponentModel.ITypeDescriptorContext> and also relies on explicit implementations to suppress false implications about the XAML type system.</span></span> <span data-ttu-id="8d7d4-149">Statik arama yardımcı yöntemlerini <xref:System.Windows.Markup.ValueSerializer>destekler.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-149">Supports the static lookup helper methods on <xref:System.Windows.Markup.ValueSerializer>.</span></span>

### <a name="ixamltyperesolver"></a><span data-ttu-id="8d7d4-150">ıxamltyperesolver</span><span class="sxs-lookup"><span data-stu-id="8d7d4-150">IXamlTypeResolver</span></span>

<span data-ttu-id="8d7d4-151">**Referans belgeleri**:<xref:System.Windows.Markup.IXamlTypeResolver></span><span class="sxs-lookup"><span data-stu-id="8d7d4-151">**Reference documentation**: <xref:System.Windows.Markup.IXamlTypeResolver></span></span>

<span data-ttu-id="8d7d4-152">**Tanım:** <xref:System.Windows.Markup> namespace, System.Xaml assembly  </span><span class="sxs-lookup"><span data-stu-id="8d7d4-152">**Defined by:**  <xref:System.Windows.Markup> namespace, System.Xaml assembly</span></span>

<span data-ttu-id="8d7d4-153">**İlgili:** Yol senaryolarını yükleme ve XAML şeması bağlamıyla etkileşim</span><span class="sxs-lookup"><span data-stu-id="8d7d4-153">**Relevant to:** Load path scenarios, and interaction with XAML schema context</span></span>

<span data-ttu-id="8d7d4-154">**Hizmet API'si:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A></span><span class="sxs-lookup"><span data-stu-id="8d7d4-154">**Service API:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A></span></span>

<span data-ttu-id="8d7d4-155">XAML yazarı bir nesne grafiğinde bir CLR nesnesi yaptığında gerekli olan XAML-CLR türü eşlemi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-155">Can influence the XAML-to-CLR type mapping that is necessary when the XAML writer constructs a CLR object in an object graph.</span></span> <span data-ttu-id="8d7d4-156"><xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>bir XAML türü ada karşılık gelen potansiyel olarak önek nitelikli dize işler ( ),<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>ve bir CLR <xref:System.Type>döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-156"><xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A> processes a potentially prefix-qualified string that corresponds to a XAML type name (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>), and returns a CLR <xref:System.Type>.</span></span> <span data-ttu-id="8d7d4-157">Türleri çözme genellikle büyük ölçüde XAML şema bağlamına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-157">Resolving types is typically heavily dependent on XAML schema context.</span></span> <span data-ttu-id="8d7d4-158">Yalnızca XAML şeması bağlamı, hangi derlemelerin yüklendiği ve bu derlemelerden hangisine tür çözümlemesi için erişilebildiği veya erişilmesi gerektiği gibi hususların farkındadır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-158">Only the XAML schema context is aware of considerations such as which assemblies are loaded, and which of these assemblies can or should be accessed for type resolution.</span></span>

### <a name="iuricontext"></a><span data-ttu-id="8d7d4-159">ıuricontext</span><span class="sxs-lookup"><span data-stu-id="8d7d4-159">IUriContext</span></span>

<span data-ttu-id="8d7d4-160">**Referans belgeleri**:<xref:System.Windows.Markup.IUriContext></span><span class="sxs-lookup"><span data-stu-id="8d7d4-160">**Reference documentation**: <xref:System.Windows.Markup.IUriContext></span></span>

<span data-ttu-id="8d7d4-161">**Tanım:** <xref:System.Windows.Markup> namespace, System.Xaml assembly  </span><span class="sxs-lookup"><span data-stu-id="8d7d4-161">**Defined by:**  <xref:System.Windows.Markup> namespace, System.Xaml assembly</span></span>

<span data-ttu-id="8d7d4-162">**İlgili:** Yolu yükleyin ve URI veya `x:Uri` değer olan üye değerlerin yol işleme kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-162">**Relevant to:** Load path and save path handling of member values that are URIs or `x:Uri` values.</span></span>

<span data-ttu-id="8d7d4-163">**Hizmet API'si:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A></span><span class="sxs-lookup"><span data-stu-id="8d7d4-163">**Service API:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A></span></span>

<span data-ttu-id="8d7d4-164">Bu hizmet, varsa, genel olarak kullanılabilir bir URI kökünü bildirir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-164">This service reports a globally available URI root, if any.</span></span> <span data-ttu-id="8d7d4-165">URI kökü, göreli URI'leri mutlak URI'lere veya tam tersi olarak çözmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-165">The URI root can be used to resolve relative URIs to absolute URIs or vice versa.</span></span> <span data-ttu-id="8d7d4-166">Bu senaryo esas olarak belirli bir çerçeve tarafından maruz kalan uygulama hizmetleri veya bir çerçevede sık kullanılan kök öğe sınıfının yetenekleri yle ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-166">This scenario is mainly relevant to application services that are exposed by a particular framework, or capabilities of a frequently used root element class in a framework.</span></span> <span data-ttu-id="8d7d4-167">Temel URI, xaml nesne swriter geçirilir ve bu hizmet tarafından bildirilen bir XAML okuyucu ayarı olarak kurulabilir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-167">The base URI can be established as a XAML reader setting, which is then passed through to the XAML object writer and reported by this service.</span></span>

### <a name="iambientprovider"></a><span data-ttu-id="8d7d4-168">ıambientprovider</span><span class="sxs-lookup"><span data-stu-id="8d7d4-168">IAmbientProvider</span></span>

<span data-ttu-id="8d7d4-169">**Referans belgeleri**:<xref:System.Xaml.IAmbientProvider></span><span class="sxs-lookup"><span data-stu-id="8d7d4-169">**Reference documentation**: <xref:System.Xaml.IAmbientProvider></span></span>

<span data-ttu-id="8d7d4-170">**Tanım:** <xref:System.Xaml> namespace, System.Xaml assembly  </span><span class="sxs-lookup"><span data-stu-id="8d7d4-170">**Defined by:**  <xref:System.Xaml> namespace, System.Xaml assembly</span></span>

<span data-ttu-id="8d7d4-171">**İlgili:** Yol işleme ve tip arama ertelemeleri veya optimizasyonlar yükleyin.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-171">**Relevant to:** Load path handling and type lookup deferrals or optimizations.</span></span>

<span data-ttu-id="8d7d4-172">**Hizmet API'leri:**  <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, üç diğer.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-172">**Service APIs:**  <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, three others.</span></span>

<span data-ttu-id="8d7d4-173">XAML'deki ortam kavramı, bir türün belirli bir üyesini ortam olarak işaretlemek için yapılan bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-173">The ambience concept in XAML is a technique for marking a particular member of a type as ambient.</span></span> <span data-ttu-id="8d7d4-174">Alternatif olarak, bir tür ortam olabilir, böylece türün bir örneğini tutan tüm özellik değerleri ortam özellikleri olarak kabul edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-174">Alternatively, a type can be ambient so that all property values that hold an instance of the type should be considered ambient properties.</span></span> <span data-ttu-id="8d7d4-175">XAML düğüm akışı boyunca daha fazla olan ve nesne grafiğindeki soyundan gelen biçimlendirme uzantıları veya tür dönüştürücüleri, yükleme zamanında ortam özelliğine veya yazı örneğine erişebilir; ya da zaman tasarrufu ortam yapısı bilgi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-175">Markup extensions or type converters that are further along the XAML node stream and that are descendants in the object graph can access the ambient property or type instance at load time; or they can use knowledge of the ambient structure at save time.</span></span> <span data-ttu-id="8d7d4-176">Bu, diğer hizmetler için veya için <xref:System.Windows.Markup.IXamlTypeResolver> `x:Type`türleri çözmek için gereken yeterlilik derecesini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-176">This can affect the degree of qualification that is needed to resolve types for other services, such as for <xref:System.Windows.Markup.IXamlTypeResolver> or for `x:Type`.</span></span> <span data-ttu-id="8d7d4-177">Ayrıca <xref:System.Xaml.AmbientPropertyValue>bakınız.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-177">See also <xref:System.Xaml.AmbientPropertyValue>.</span></span>

### <a name="ixamlschemacontextprovider"></a><span data-ttu-id="8d7d4-178">ıxamlschemacontextprovider</span><span class="sxs-lookup"><span data-stu-id="8d7d4-178">IXamlSchemaContextProvider</span></span>

<span data-ttu-id="8d7d4-179">**Referans belgeleri**:<xref:System.Xaml.IXamlSchemaContextProvider></span><span class="sxs-lookup"><span data-stu-id="8d7d4-179">**Reference documentation**: <xref:System.Xaml.IXamlSchemaContextProvider></span></span>

<span data-ttu-id="8d7d4-180">**Tanım:** <xref:System.Xaml> namespace, System.Xaml assembly  </span><span class="sxs-lookup"><span data-stu-id="8d7d4-180">**Defined by:**  <xref:System.Xaml> namespace, System.Xaml assembly</span></span>

<span data-ttu-id="8d7d4-181">**İlgili:** Yükleme yolu ve bir XAML türünü destek türüne çözmesi gereken herhangi bir işlem.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-181">**Relevant to:** Load path, and any operation that must resolve a XAML type to a backing type.</span></span>

<span data-ttu-id="8d7d4-182">**Hizmet API'si:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A></span><span class="sxs-lookup"><span data-stu-id="8d7d4-182">**Service API:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A></span></span>

<span data-ttu-id="8d7d4-183">XAML şeması bağlamı herhangi bir erteleme yük işlemleri için gereklidir, çünkü aynı şema bağlamı ertelenmiş içeriği tümleştirmek için ertelenmiş alanda hareket etmelidir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-183">XAML schema context is necessary for any defer load operations, because the same schema context must act on the deferred area in order to integrate the deferred content.</span></span> <span data-ttu-id="8d7d4-184">XAML şema bağlamının rolü hakkında daha fazla bilgi için Bkz. [XAML Hizmetleri.](../../../api/index.md)</span><span class="sxs-lookup"><span data-stu-id="8d7d4-184">For more information about the role of the XAML schema context, see [XAML Services](../../../api/index.md).</span></span>

### <a name="irootobjectprovider"></a><span data-ttu-id="8d7d4-185">ırootobjectprovider</span><span class="sxs-lookup"><span data-stu-id="8d7d4-185">IRootObjectProvider</span></span>

<span data-ttu-id="8d7d4-186">**Referans belgeleri**:<xref:System.Xaml.IRootObjectProvider></span><span class="sxs-lookup"><span data-stu-id="8d7d4-186">**Reference documentation**: <xref:System.Xaml.IRootObjectProvider></span></span>

<span data-ttu-id="8d7d4-187">**Tanım:** <xref:System.Xaml> namespace, System.Xaml assembly  </span><span class="sxs-lookup"><span data-stu-id="8d7d4-187">**Defined by:**  <xref:System.Xaml> namespace, System.Xaml assembly</span></span>

<span data-ttu-id="8d7d4-188">**İlgili:** Yük yolu.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-188">**Relevant to:** Load path.</span></span>

<span data-ttu-id="8d7d4-189">**Hizmet API'si:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A></span><span class="sxs-lookup"><span data-stu-id="8d7d4-189">**Service API:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A></span></span>

<span data-ttu-id="8d7d4-190">Hizmet, belirli bir çerçeve tarafından veya bir çerçevede sık kullanılan kök öğe sınıfının yetenekleri tarafından ortaya çıkarılan uygulama hizmetleriyle ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-190">The service is relevant to application services that are exposed by a particular framework or by capabilities of a frequently used root element class in a framework.</span></span> <span data-ttu-id="8d7d4-191">Kök nesneyi elde etmek için bir senaryo kod arkasında ve olay kablolama bağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-191">One scenario for obtaining the root object is connecting code-behind and event wiring.</span></span> <span data-ttu-id="8d7d4-192">Örneğin, WPF uygulaması, `x:Class` XAML biçimlendirmesinde başka bir konumda bulunan herhangi bir olay işleyiciözünün biçimlendirme derlemesi ve kablolama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-192">For example, the WPF implementation of `x:Class` is used for markup compile and wiring of any event handler attribute that is found at any other position in the XAML markup.</span></span> <span data-ttu-id="8d7d4-193">Biçimlendirme derlemesi için biçimlendirme ve kod arkası tanımlı kısmi sınıfların bağlantı noktası kök öğededir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-193">The connection point of markup and code-behind defined partial classes for markup compile is at the root element.</span></span>

### <a name="ixamlnamespaceresolver"></a><span data-ttu-id="8d7d4-194">ıxamlnamespaceresolver</span><span class="sxs-lookup"><span data-stu-id="8d7d4-194">IXamlNamespaceResolver</span></span>

<span data-ttu-id="8d7d4-195">**Referans belgeleri**:<xref:System.Xaml.IXamlNamespaceResolver></span><span class="sxs-lookup"><span data-stu-id="8d7d4-195">**Reference documentation**: <xref:System.Xaml.IXamlNamespaceResolver></span></span>

<span data-ttu-id="8d7d4-196">**Tanım:** <xref:System.Xaml> namespace, System.Xaml assembly  </span><span class="sxs-lookup"><span data-stu-id="8d7d4-196">**Defined by:**  <xref:System.Xaml> namespace, System.Xaml assembly</span></span>

<span data-ttu-id="8d7d4-197">**İlgili:** Yolu yükleyin, yolu kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-197">**Relevant to:** Load path, save path.</span></span>

<span data-ttu-id="8d7d4-198">**Servis API:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> yük <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> yolu için, kaydet yolu için.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-198">**Service API:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> for load path, <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> for save path.</span></span>

<span data-ttu-id="8d7d4-199"><xref:System.Xaml.IXamlNamespaceResolver>bir XAML ad alanı tanımlayıcısı / URI kökenli XAML işaretleme eşlenen olarak öneki dayalı döndürebilir bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-199"><xref:System.Xaml.IXamlNamespaceResolver> is a service that can return a XAML namespace identifier / URI based on its prefix as mapped in the originating XAML markup.</span></span>

### <a name="iprovidevaluetarget"></a><span data-ttu-id="8d7d4-200">ıprovidevaluetarget</span><span class="sxs-lookup"><span data-stu-id="8d7d4-200">IProvideValueTarget</span></span>

<span data-ttu-id="8d7d4-201">**Referans belgeleri**:<xref:System.Windows.Markup.IProvideValueTarget></span><span class="sxs-lookup"><span data-stu-id="8d7d4-201">**Reference documentation**: <xref:System.Windows.Markup.IProvideValueTarget></span></span>

<span data-ttu-id="8d7d4-202">**Tanım:** <xref:System.Windows.Markup> namespace, System.Xaml assembly  </span><span class="sxs-lookup"><span data-stu-id="8d7d4-202">**Defined by:**  <xref:System.Windows.Markup> namespace, System.Xaml assembly</span></span>

<span data-ttu-id="8d7d4-203">**İlgili:** Yolu yükleyin ve yolu kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-203">**Relevant to:** Load path and save path.</span></span>

<span data-ttu-id="8d7d4-204">**Servis API'leri:**<xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  </span><span class="sxs-lookup"><span data-stu-id="8d7d4-204">**Service APIs:**  <xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.</span></span>

<span data-ttu-id="8d7d4-205"><xref:System.Windows.Markup.IProvideValueTarget>yük zamanında nerede hareket ettiği neresinde olduğu hakkında bağlam elde etmek için bir tür dönüştürücü veya biçimlendirme uzantısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-205"><xref:System.Windows.Markup.IProvideValueTarget> enables a type converter or markup extension to obtain context about where it is acting at load time.</span></span> <span data-ttu-id="8d7d4-206">Uygulamalar, kullanımı geçersiz ksaymak için bu bağlamı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-206">Implementations might use this context to invalidate a usage.</span></span> <span data-ttu-id="8d7d4-207">Örneğin, WPF gibi bazı biçimlendirme uzantıları içinde <xref:System.Windows.DynamicResourceExtension>mantık vardır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-207">For example, WPF has logic inside some of its markup extensions such as <xref:System.Windows.DynamicResourceExtension>.</span></span> <span data-ttu-id="8d7d4-208">Mantık, uzantının yalnızca bağımlılık özelliklerini (veya diğer bağımlılık dışı özelliklerin kısa bir listesini) ayarlamak için kullanıldığından emin olmak için denetimi <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> denetler.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-208">The logic checks the <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> to make sure that the extension is only used to set dependency properties (or a short list of other non-dependency properties).</span></span>

### <a name="ixamlnameresolver"></a><span data-ttu-id="8d7d4-209">ıxamlnameresolver</span><span class="sxs-lookup"><span data-stu-id="8d7d4-209">IXamlNameResolver</span></span>

<span data-ttu-id="8d7d4-210">**Referans belgeleri**:<xref:System.Xaml.IXamlNameResolver></span><span class="sxs-lookup"><span data-stu-id="8d7d4-210">**Reference documentation**: <xref:System.Xaml.IXamlNameResolver></span></span>

<span data-ttu-id="8d7d4-211">**Tanım:** <xref:System.Xaml> namespace, System.Xaml assembly  </span><span class="sxs-lookup"><span data-stu-id="8d7d4-211">**Defined by:**  <xref:System.Xaml> namespace, System.Xaml assembly</span></span>

<span data-ttu-id="8d7d4-212">**İlgili:** Yol nesnesi grafik tanımını yükleyin, "veya `x:Name` `x:Reference`çerçeveye özgü tekniklerle" tanımlanan nesneleri çözümle.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-212">**Relevant to:** Load path object graph definition, resolving objects identified by `x:Name`, `x:Reference`, or framework-specific techniques.</span></span>

<span data-ttu-id="8d7d4-213">**Hizmet API'leri:**  <xref:System.Xaml.IXamlNameResolver.Resolve%2A>; ileri referanslarla başa çıkma gibi daha gelişmiş senaryolar için diğer API'ler.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-213">**Service APIs:**  <xref:System.Xaml.IXamlNameResolver.Resolve%2A>; other APIs for more advanced scenarios such as dealing with forward references.</span></span>

<span data-ttu-id="8d7d4-214">.NET XAML Hizmetleri'nin `x:Reference` işleme uygulaması bu hizmete dayanır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-214">.NET XAML Services implementation of `x:Reference` handling relies on this service.</span></span> <span data-ttu-id="8d7d4-215">Çerçeveyi destekleyen belirli çerçeveler veya araçlar, bu<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> hizmeti işleme veya eşdeğer (atfedilen) mülk işleme için `x:Name` kullanır.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-215">Specific frameworks or tools that support the framework use this service for `x:Name` handling or equivalent (<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> attributed) property handling.</span></span>

### <a name="idestinationtypeprovider"></a><span data-ttu-id="8d7d4-216">IDestinationTypeProvider</span><span class="sxs-lookup"><span data-stu-id="8d7d4-216">IDestinationTypeProvider</span></span>

<span data-ttu-id="8d7d4-217">**Referans belgeleri**:<xref:System.Xaml.IDestinationTypeProvider></span><span class="sxs-lookup"><span data-stu-id="8d7d4-217">**Reference documentation**: <xref:System.Xaml.IDestinationTypeProvider></span></span>

<span data-ttu-id="8d7d4-218">**Tanım:** <xref:System.Xaml> namespace, System.Xaml assembly  </span><span class="sxs-lookup"><span data-stu-id="8d7d4-218">**Defined by:**  <xref:System.Xaml> namespace, System.Xaml assembly</span></span>

<span data-ttu-id="8d7d4-219">**İlgili:** Dolaylı CLR türü bilgilerin yük yolu çözünürlüğü.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-219">**Relevant to:** Load path resolution of indirect CLR type information.</span></span>

<span data-ttu-id="8d7d4-220">**Hizmet API'si:**<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A></span><span class="sxs-lookup"><span data-stu-id="8d7d4-220">**Service API:** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A></span></span>

<span data-ttu-id="8d7d4-221">Daha fazla bilgi için bkz. <xref:System.Xaml.IDestinationTypeProvider>.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-221">For more information, see <xref:System.Xaml.IDestinationTypeProvider>.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d7d4-222">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d7d4-222">See also</span></span>

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [<span data-ttu-id="8d7d4-223">XAML Biçimlendirme Uzantılarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8d7d4-223">Markup Extensions for XAML Overview</span></span>](markup-extensions-overview.md)
- [<span data-ttu-id="8d7d4-224">XAML Tür Dönüştürücülerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8d7d4-224">Type Converters for XAML Overview</span></span>](type-converters-overview.md)
